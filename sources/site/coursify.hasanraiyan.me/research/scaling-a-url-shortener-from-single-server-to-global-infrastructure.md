# Source: https://coursify.hasanraiyan.me/research/scaling-a-url-shortener-from-single-server-to-global-infrastructure

Scaling a URL Shortener: From Single Server to Global Infrastructure

# 

Scaling a URL Shortener: From Single Server to Global Infrastructure

Verified Sources

Jun 17, 2026

## AI Summary

A URL shortener seems deceptively simple — take a long URL, return a short one, and redirect when clicked. But beneath this simplicity lies a rich set of distributed systems challenges: **unique ID generation at scale**, **sub-50ms redirection latency**, **database sharding for billions of records**, and **caching strategies for read-heavy workloads**.

Real-world URL shorteners like Bitly handle **billions of redirects** with a read-to-write ratio of approximately **200:1** . At that scale, every architectural decision — from encoding strategy to sharding key — has profound implications for availability, latency, and cost.

This course section provides a comprehensive, production-oriented guide to scaling a URL shortener, covering capacity estimation, key generation algorithms, database sharding, caching, rate limiting, and analytics pipelines.

## Footnotes

1. [System Design: Scalable URL Shortener Service like TinyURL](https://medium.com/@sandeep4.verma/system-design-scalable-url-shortener-service-like-tinyurl-106f30f23a82) - Comprehensive capacity estimation, sharding, and caching strategies for URL shorteners. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1)
 

#### Design a URL Shortener (Bitly) - System Design Interview

### Capacity Estimation — Back-of-the-Envelope Calculations

Before designing, we must quantify the problem. Let's establish baseline numbers for a service expected to handle **100 million new URLs per month** over a 10-year lifetime [2]():

| Metric | Calculation | Result |
| --- | --- | --- |
| New URLs/sec | 100×106/(30×24×3600)100 \\times 10^6 / (30 \\times 24 \\times 3600)100×106/(30×24×3600) | ~40 writes/s |
| Redirects/sec (200:1 ratio) | 40×20040 \\times 20040×200 | ~8,000 reads/s |
| Total URLs (10 years) | 100×106×12×10100 \\times 10^6 \\times 12 \\times 10100×106×12×10 | 12 billion |
| Storage (500 bytes/record, 100 yrs) | 120×109×500120 \\times 10^9 \\times 500120×109×500 bytes | ~60 TB |
| Cache memory (80/20 rule) | 0.2×700M×5000.2 \\times 700M \\times 5000.2×700M×500 bytes/day | ~70 GB |

The read-heavy nature (200:1) immediately tells us that **caching is non-negotiable** and that the database must be optimized for fast key-value lookups. The 60 TB storage requirement means a **single database node cannot serve this** — sharding is essential .

### The Base62 Encoding Space

A Base62 encoding scheme determines the character set and thus the addressable space of short URLs:

627\=3,521,614,606,208≈3.5 trillion unique keys62^7 = 3{,}521{,}614{,}606{,}208 \\approx 3.5 \\text{ trillion unique keys}627\=3,521,614,606,208≈3.5 trillion unique keys

With 7 characters in Base62, we get approximately **3.5 trillion** unique short URLs — far exceeding the 365 billion URLs expected over 10 years [2]().

| Key Length | Combinations |
| --- | --- |
| 1 | 62 |
| 2 | 3,844 |
| 3 | 238,328 |
| 6 | ~56.8 billion |
| **7** | **~3.5 trillion** |

## Footnotes

1. [System Design: Scalable URL Shortener Service like TinyURL](https://medium.com/@sandeep4.verma/system-design-scalable-url-shortener-service-like-tinyurl-106f30f23a82) - Comprehensive capacity estimation, sharding, and caching strategies for URL shorteners. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1)
 
2. [Design URL Shortener | System Design Interview | AlgoMaster.io](https://algomaster.io/learn/system-design-interviews/design-url-shortener) - Key generation strategies comparison, distributed ID generation, and fast URL redirection architecture. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-2) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-2-2)
 
3. [System Design Interview Question: Design URL Shortener - Hayk Simonyan](https://hayksimonyan.substack.com/p/system-design-interview-question-8ea) - Full system design walkthrough with database scaling, replication, and sharding recommendations. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-3)
 
4. [Design a URL Shortener - ByteByteGo](https://bytebytego.com/courses/system-design-interview/design-a-url-shortener) - Base62 encoding deep dive, API design, and ID generation flow diagrams. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 

### 

Read vs Write Traffic Distribution

Estimated QPS for a URL shortener handling 100M URLs/month

### URL Shortening Key Generation Strategies

1. 1
 
 Step 1
 
 Base62 Counter Encoding
 
 Maintain a monotonically increasing counter in the database. Each new URL gets the next counter value, which is then encoded to a 7-character Base62 string. For example, ID `2009215674938` encodes to `zn9edcu`. This guarantees uniqueness and is simple to implement, but the centralized counter becomes a **single point of failure and a throughput bottleneck** at scale [2]().
 
 ## Footnotes
 
 1. [Design a URL Shortener - ByteByteGo](https://bytebytego.com/courses/system-design-interview/design-a-url-shortener) - Base62 encoding deep dive, API design, and ID generation flow diagrams. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
 2. [Design a URL Shortener - AlgoMaster Blog](https://blog.algomaster.io/p/design-a-url-shortener) - MD5 hashing approach, collision handling, and predictability mitigations. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5)
 
 
2. 2
 
 Step 2
 
 MD5 Hashing + Base62
 
 Compute an MD5 hash of the long URL, then take the first 6–7 characters of the Base62-encoded hash. This is deterministic — the same long URL always produces the same short URL, enabling deduplication. However, **collisions are inevitable** due to truncation, requiring retry logic or collision resolution. MD5 produces a 128-bit hash; taking only a subset significantly increases collision probability .
 
 ## Footnotes
 
 1. [Design a URL Shortener - ByteByteGo](https://bytebytego.com/courses/system-design-interview/design-a-url-shortener) - Base62 encoding deep dive, API design, and ID generation flow diagrams. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
 
3. 3
 
 Step 3
 
 Key Generation Service (KGS)
 
 A dedicated Key Generation Service maintains a pool of pre-generated unique keys. A separate Key Generation Service (KGS) server pushes batches of pre-generated keys to a key database. Each application server fetches a **range of keys** (e.g., 1,000 keys at a time) and uses them locally. This eliminates race conditions because no two servers ever get the same key range. The KGS itself is a SPOF, so it must be replicated [2]().
 
 ## Footnotes
 
 1. [Design URL Shortener | System Design Interview | AlgoMaster.io](https://algomaster.io/learn/system-design-interviews/design-url-shortener) - Key generation strategies comparison, distributed ID generation, and fast URL redirection architecture. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-2)
 
 2. [System Design Interview Question: Design URL Shortener - Hayk Simonyan](https://hayksimonyan.substack.com/p/system-design-interview-question-8ea) - Full system design walkthrough with database scaling, replication, and sharding recommendations. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-3)
 
 
4. 4
 
 Step 4
 
 Distributed ID Generation (Snowflake-style)
 
 "Use a distributed ID generator like Twitter's Snowflake to produce globally unique, roughly time-ordered 64-bit IDs without any central coordination. Each worker generates IDs independently using a combination of **timestamp + worker ID + sequence number**. The resulting integer is then Base62-encoded. This approach is **highly scalable** — throughput increases linearly with the number of workers — but is sensitive to clock skew [2]()."
 
 ## Footnotes
 
 1. [System Design Interview Question: Design URL Shortener - Hayk Simonyan](https://hayksimonyan.substack.com/p/system-design-interview-question-8ea) - Full system design walkthrough with database scaling, replication, and sharding recommendations. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-3)
 
 2. [Design a URL Shortener - AlgoMaster Blog](https://blog.algomaster.io/p/design-a-url-shortener) - MD5 hashing approach, collision handling, and predictability mitigations. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5)
 
 

Python

JavaGo

`1import string 2 3BASE62 = string.digits + string.ascii_letters 4 5def base62_encode(num: int) -> str: 6    if num == 0: 7        return BASE62[0] 8    result = [] 9    while num > 0: 10        num, remainder = divmod(num, 62) 11        result.append(BASE62[remainder]) 12    return ''.join(reversed(result)) 13 14def base62_decode(short: str) -> int: 15    lookup = {c: i for i, c in enumerate(BASE62)} 16    num = 0 17    for char in short: 18        num = num * 62 + lookup[char] 19    return num 20 21# Example 22print(base62_encode(2009215674938))  # zn9edcu 23print(base62_decode('zn9edcu'))      # 2009215674938`

### Database Sharding Strategies

When a single database can no longer handle the storage or query load, we must shard the data. The choice of shard key fundamentally determines scalability [2]():

#### 1\. Hash-Based Sharding on Short URL

Apply a hash function to the short URL key and use `hash(short_url) % N_shards` to determine the target shard. This yields **even data distribution** but complicates range queries. MongoDB supports hashed sharding natively, computing the hash automatically during query resolution .

#### 2\. Range-Based Sharding

Shard by key ranges (e.g., keys `a*` → Shard 1, `b*` → Shard 2). This can cause **hotspots** when writes cluster in one range (e.g., sequential IDs all map to the same shard). Not recommended for counter-based systems.

#### 3\. Machine-ID Prefix Sharding

Each application server is assigned a unique machine ID prefix (1 character from Base62). That prefix doubles as the shard key: all URLs created by Server A go to Shard A. This ensures **write-path independence** — each server writes to exactly one shard, enabling linear scalability. The downside is uneven distribution if some servers handle more traffic .

For read scalability, each shard can use **master-slave replication** — the master handles writes and replicas serve reads. With 3 shards each replicated 3 times, you get 9 read-capable nodes distributing ~8,000 reads/s comfortably .

## Footnotes

1. [System Design: Scalable URL Shortener Service like TinyURL](https://medium.com/@sandeep4.verma/system-design-scalable-url-shortener-service-like-tinyurl-106f30f23a82) - Comprehensive capacity estimation, sharding, and caching strategies for URL shorteners. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-1-2)
 
2. [Design URL Shortener Solution - System Design School](https://systemdesignschool.io/problems/url-shortener/solution) - Machine-ID prefix sharding, write-path independence, and horizontal scaling patterns. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-6) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-6-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-6-3)
 

#### Race Condition in Distributed Key Generation

When multiple application servers independently generate short URLs using the same algorithm (e.g., counter + Base62), a race condition can occur. Two servers may read the same counter value, increment it, and produce identical short URLs for different long URLs. Always use a Key Generation Service (KGS), distributed ID generator, or database-level unique constraints with retry logic to prevent this .

## Footnotes

1. [Design a URL Shortener - ByteByteGo](https://bytebytego.com/courses/system-design-interview/design-a-url-shortener) - Base62 encoding deep dive, API design, and ID generation flow diagrams. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 

more...

### Caching Architecture for Hot URLs

With a 200:1 read-to-write ratio, caching is the single most impactful optimization. Following the **Pareto principle** (80/20 rule), caching 20% of URLs serves ~80% of redirect traffic [2]():

| Metric | Value |
| --- | --- |
| Daily redirect requests | ~700 million |
| 20% cached | ~140 million unique keys |
| Memory per entry | ~500 bytes |
| **Total cache memory** | **~70 GB** |

A Redis cluster with multiple nodes can easily hold this in memory. The canonical flow for redirects:

1. Client requests `GET /{short_code}`
2. Server checks **Redis cache** → **cache hit**: return `302 Found` with the long URL in under **5 ms**
3. **Cache miss**: query the database, populate the cache, then return `302`

#### Cache Eviction Policies

- **LRU (Least Recently Used)**: Evict the least-accessed entry. Ideal for URL shorteners where popularity follows a power-law distribution.
- **TTL-based**: Set expiration matching link TTL. Expired short URLs are automatically purged, freeing memory for active entries.
- **Write-through cache**: On URL creation, write both to database and cache to prevent cold-start misses for new popular links.

#### Redirect Headers: 301 vs 302

This is a critical design choice for analytics :

- **301 (Moved Permanently)**: Browser caches the redirect. Subsequent clicks bypass your server entirely — **no analytics** possible for those clicks.
- **302 (Found / Temporary)**: Browser always hits your server first. Every click is tracked, but adds latency per redirect.

**Production choice**: Use **302** for analytics-driven services. The marginal latency cost (~10ms) is worth the data visibility.

## Footnotes

1. [Design URL Shortener | System Design Interview | AlgoMaster.io](https://algomaster.io/learn/system-design-interviews/design-url-shortener) - Key generation strategies comparison, distributed ID generation, and fast URL redirection architecture. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-2)
 
2. [Designing URL Shortener Systems: From TinyURL to Bitly Scale - DEV Community](https://dev.to/sgchris/designing-url-shortener-systems-from-tinyurl-to-bitly-scale-1ip5) - Production architecture, database sharding, caching strategies, and rate limiting. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-7)
 
3. [URL Shorteners and Phishing: Risks and How to Verify - CaptainDNS](https://www.captaindns.com/en/blog/url-shorteners-security-risks-phishing-attack-vector) - 301 vs 302 redirect implications for analytics and security considerations. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-8)
 

### 

Scaling Lifecycle of a URL Shortener

#### Single Server

Phase 1

One web server + one database (PostgreSQL/MySQL). Serves ~100 QPS. Works for MVP but is a SPOF. Database stores short\_url → long\_url mapping."

#### Load Balancer + Cache

Phase 2

Add a load balancer distributing traffic across multiple stateless API servers. Introduce Redis cache for hot URLs. Handles ~10K QPS with sub-50ms p99 latency."

#### Database Sharding

Phase 3

Shard the database using hash-based or machine-ID-prefix sharding. Each shard uses master-slave replication for read scalability. Supports 60TB+ storage across shards."

#### Distributed ID Generation

Phase 4

Replace centralized counter with Key Generation Service (KGS) or Snowflake-style distributed IDs. Eliminates ID generation bottleneck and race conditions."

#### Global Distribution

Phase 5

Deploy across multiple geographic regions with CDN edge caching. Use geo-DNS to route users to the nearest data center. Analytics pipeline via Kafka for async click tracking."

### Rate Limiting and Abuse Prevention

At scale, URL shorteners become prime targets for abuse — phishing links, spam distribution, and denial-of-service attacks. A robust rate limiting strategy is essential :

#### Sliding Window Log Algorithm (Redis-Based)

Track request timestamps using Redis sorted sets. Each request adds a timestamp entry; old entries outside the window are pruned. The count of remaining entries determines whether the request is allowed.

| Rate Limit Dimension | Typical Limit | Purpose |
| --- | --- | --- |
| Per IP | 100 requests/min | Prevent spam bots |
| Per User | 30 URL creations/hour | Limit account abuse |
| Global | 50K req/s | Protect infrastructure |

**Redis Key Design** :

| Pattern | Type | TTL | Purpose |
| --- | --- | --- | --- |
| `url:{shortCode}` | String | 7 days | URL mapping cache |
| `clicks:{shortCode}` | String | None | Click counters |
| `rate:ip:{ip}` | Sorted Set | 60s | Per-IP rate limiting |
| `rate:user:{userId}` | Sorted Set | 60s | Per-user rate limiting |

#### Additional Security Measures

- **URL validation**: Reject malformed or non-HTTP(S) URLs at the API layer
- **Malware scanning**: Asynchronously scan destination URLs against threat databases (Google Safe Browsing API)
- **Custom alias restrictions**: Reserve system paths (e.g., `admin`, `api`, `login`) to prevent namespace squatting
- **Obfuscation**: Shuffle IDs before Base62 encoding to prevent enumeration attacks where an attacker can guess URLs by incrementing a counter

## Footnotes

1. [Scalable URL Shortener - GitHub (Jay-Lokhande)](https://github.com/Jay-Lokhande/scalable-url-shortener) - Production-ready architecture with Redis key design, rate limiting strategy, and failure handling patterns. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-9) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-9-2)
 
2. [Design a URL Shortener - AlgoMaster Blog](https://blog.algomaster.io/p/design-a-url-shortener) - MD5 hashing approach, collision handling, and predictability mitigations. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5)
 

#### Cache Failure Strategy: Fail-Open

When Redis goes down, use a **fail-open** strategy: allow requests to pass through to the database rather than rejecting all traffic. It's better to allow some spike in database load than to deny service to all legitimate users. Monitor cache hit ratio and alert when it drops below 80% — a degraded cache means the database is absorbing far more load than it was designed for .

## Footnotes

1. [Scalable URL Shortener - GitHub (Jay-Lokhande)](https://github.com/Jay-Lokhande/scalable-url-shortener) - Production-ready architecture with Redis key design, rate limiting strategy, and failure handling patterns. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-9)
 

more...

### Analytics Pipeline: Tracking Clicks at Scale

Analytics is often the **commercial justification** for URL shortening services. Every redirect is an event to be captured, processed, and visualized. Processing analytics **synchronously** in the redirect path would add unacceptable latency .

#### Asynchronous Analytics Architecture

**Click Event Payload:**

`1{ 2  "short_code": "abc123", 3  "timestamp": 1718000000, 4  "ip_hash": "a1b2c3", 5  "user_agent": "Mozilla/5.0...", 6  "referrer": "https://twitter.com", 7  "geo_country": "US" 8}`

The analytics pipeline uses a **fire-and-forget** pattern: the API server publishes the click event to a Kafka or RabbitMQ queue and immediately returns the redirect. The analytics service consumes events asynchronously, aggregates them (e.g., per-hour click counts per short URL), and persists results in a columnar analytics database optimized for time-series queries .

**Key design decisions:**

- **Don't block the redirect** on analytics writes — latency budget is already tight at <50ms p99
- **Hash personally identifiable information** (IP addresses) for privacy compliance
- **Use counter caching in Redis** (`clicks:{shortCode}`) and periodically flush to the analytics database
- **Graceful degradation**: if the analytics queue is unavailable, **the redirect still works** — drop the event, don't fail the request

## Footnotes

1. [Scalable URL Shortener - GitHub (Jay-Lokhande)](https://github.com/Jay-Lokhande/scalable-url-shortener) - Production-ready architecture with Redis key design, rate limiting strategy, and failure handling patterns. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-9) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-9-2)
 

### 

URL Shortener Read/Write Ratio

Typical traffic distribution for a production URL shortener

### Advanced Scaling Topics

What database should I use for the URL mapping store?

How do I handle link expiration without scanning the entire database?

How do I deduplicate long URLs efficiently?

How does geo-distribution work for a global URL shortener?

What about CDN-based caching for redirects?

### Knowledge Check

Question 1 of 5

Q1Single choice

A URL shortener needs to support 3.5 trillion unique short URLs. What is the minimum key length required using Base62 encoding?

5 characters (625≈91662^5 \\approx 916625≈916 million)

6 characters (626≈56.862^6 \\approx 56.8626≈56.8 billion)

7 characters (627≈3.562^7 \\approx 3.5627≈3.5 trillion)

8 characters (628≈21862^8 \\approx 218628≈218 trillion)

BackNext

### Summary of Key Architecture Decisions

| Decision | Recommendation | Reasoning |
| --- | --- | --- |
| Key generation | Distributed ID (Snowflake) or KGS | Avoids SPOF and race conditions at scale |
| Encoding | Base62, 7 characters | 627≈3.5T62^7 \\approx 3.5T627≈3.5T unique keys—sufficient for 10+ years |
| Database | Cassandra / DynamoDB (or sharded PostgreSQL) | Horizontal scalability for 60TB+ |
| Sharding | Hash-based or machine-ID prefix | Even distribution / write-path independence |
| Cache | Redis cluster, ~70GB, LRU eviction | Serves 80% of reads from memory |
| Redirect | HTTP 302 (temporary) | Required for click analytics |
| Analytics | Async pipeline via Kafka | Never block the redirect path |
| Rate limiting | Sliding window log in Redis | Per-user and per-IP limits prevent abuse |
| Cache failure | Fail-open | Prefer degraded DB load over total outage |
| Geo-distribution | Multi-region with local caches | Sub-50ms global redirect latency |

Scaling a URL shortener is a masterclass in applying distributed systems principles — the simplicity of the problem domain allows each challenge (uniqueness, consistency, availability, latency) to be isolated and addressed with well-understood patterns.

## Explore Related Topics

[1\\ \\ LangChain vs LangGraph: A Comprehensive Comparison\\ \\ LangChain and LangGraph are complementary frameworks in the LangChain ecosystem: LangChain offers fast, linear pipeline composition via LCEL, while LangGraph provides a graph‑based runtime with persistent state, loops, branching, and human‑in‑the‑loop capabilities.\\ \\ - LangChain’s modular components (models, prompts, memory, tools) are combined with the pipe operator `|` to build simple to moderate linear workflows such as retrieve‑summarize‑answer. - LangGraph introduces three primitives—State, Nodes, and Edges—enabling cycles, conditional branches, multi‑agent coordination, and checkpoint‑driven fault tolerance. - State management differs: LangChain relies on chain‑scoped Memory; LangGraph uses a global State object with checkpointers that support time‑travel debugging and rollback. - Decision guidance: choose LangChain for straightforward RAG or Q&A bots; adopt LangGraph when you need loops, branching, persistent state, or production‑grade resilience.\\ \\ Statet+1\=merge(Statet, ⋃n∈Nodestfn(Statet))\\text{State}\_{t+1} = \\text{merge}\\big(\\text{State}\_t,\\ \\bigcup\_{n \\in \\text{Nodes}\_t} f\_n(\\text{State}\_t)\\big)Statet+1​\=merge(Statet​, ⋃n∈Nodest​​fn​(Statet​))](https://coursify.hasanraiyan.me/research/langchain-vs-langgraph-a-comprehensive-comparison) [2\\ \\ Address Translation in Paging and Why Page Size Is Usually a Power of Two](https://coursify.hasanraiyan.me/research/address-translation-in-paging-and-why-page-size-is-usually-a-power-of-two)

[![Coursify logo](https://coursify.hasanraiyan.me/_next/image?url=%2Fimages%2Fapps%2Fcoursify.png&w=48&q=75)Browse all research articles](https://coursify.hasanraiyan.me/research)