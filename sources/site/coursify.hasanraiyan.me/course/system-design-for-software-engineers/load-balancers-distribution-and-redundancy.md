# Source: https://coursify.hasanraiyan.me/course/system-design-for-software-engineers/load-balancers-distribution-and-redundancy

# Load Balancers: Distribution and Redundancy

## Load Balancers: The Gatekeepers of Scalability

In a distributed system, no single server can handle infinite traffic. As your application grows from hundreds to millions of users, you must transition from a single server (vertical scaling) to a cluster of servers (horizontal scaling). This transition introduces a fundamental problem: **How do you decide which server should handle an incoming request?**

Enter the **Load Balancer (LB)**. A load balancer acts as a reverse proxy, sitting between the client and the server pool. It accepts incoming traffic and distributes it across multiple backend servers based on various algorithms.

### Why Use a Load Balancer?

1. **Scalability**: Seamlessly add or remove servers from the pool without downtime.
2. **Availability**: If one server fails, the load balancer reroutes traffic to healthy instances (automatic failover).
3. **Efficiency**: Prevents any single server from becoming a bottleneck by evening out the workload.
4. **Security**: Can act as a shield, hiding the IP addresses of internal servers and providing a single point for SSL termination and DDoS mitigation.

### Layer 4 vs. Layer 7 Load Balancing

Load balancers operate at different levels of the OSI model, primarily Layer 4 (Transport) and Layer 7 (Application).

#### Layer 4 (L4) Load Balancing

L4 load balancers make decisions based on network information like **IP addresses and TCP/UDP ports**. They do not look at the content of the packets (the HTTP headers, cookies, or payload).

- **Pros**: Extremely fast (low latency), low resource overhead, handles any protocol.
- **Cons**: Cannot perform content-aware routing (e.g., routing based on a URL path).

#### Layer 7 (L7) Load Balancing

L7 load balancers (also known as Application Load Balancers) make decisions based on the **actual content of the request**, such as HTTP headers, cookies, session IDs, or the URL path (`/api` vs `/static`).

- **Pros**: Highly flexible, supports session persistence (sticky sessions), enables A/B testing and canary deployments.
- **Cons**: More resource-intensive (needs to decrypt/buffer the request), slightly higher latency.

### Configuring a Basic Nginx Load Balancer

1. 1
 
 Step 1
 
 Install Nginx
 
 On a Linux server, install Nginx using the package manager. For example, on Ubuntu: `sudo apt update && sudo apt install nginx`. This server will act as your entry point.
 
2. 2
 
 Step 2
 
 Define the Backend Server Pool
 
 Open the Nginx configuration file (usually `/etc/nginx/nginx.conf` or a site-specific file in `/etc/nginx/sites-available/`). Use the `upstream` directive to list your backend servers.
 
 `1upstream my_app { 2    server 10.0.0.1; 3    server 10.0.0.2; 4    server 10.0.0.3; 5}`
 
3. 3
 
 Step 3
 
 Configure the Reverse Proxy
 
 Inside the `server` block, use the `proxy_pass` directive to point traffic to your defined upstream group.
 
 `1server { 2    listen 80; 3    location / { 4        proxy_pass http://my_app; 5    } 6}`
 
4. 4
 
 Step 4
 
 Choose a Balancing Algorithm
 
 By default, Nginx uses Round Robin. You can change this by adding an algorithm keyword inside the `upstream` block. For example, use `least_conn;` to send requests to the server with the fewest active connections.
 
5. 5
 
 Step 5
 
 Apply and Test
 
 Check the configuration for errors with `sudo nginx -t`. If successful, reload the service with `sudo systemctl reload nginx`. Your load balancer is now active!
 

### Load Balancing Algorithms

Choosing the right algorithm is critical for optimal performance:

1. **Round Robin**: Requests are distributed sequentially. Best when all servers have similar hardware and the tasks are uniform.
2. **Least Connections**: Sends requests to the server with the fewest active connections. Ideal for long-lived connections (e.g., WebSockets).
3. **IP Hash**: The client's IP address is hashed to determine the server. This ensures a client always goes to the same server (session persistence).
4. **Weighted Round Robin**: Allows you to assign weights to servers based on their capacity (e.g., a server with 32GB RAM gets twice as much traffic as one with 16GB).

### Health Checks and Reliability

A load balancer is only useful if it knows which servers are actually alive. **Health Checks** involve the LB periodically pinging the backend servers.

- **Passive Health Checks**: The LB notices if a request to a server fails and temporarily stops sending traffic there.
- **Active Health Checks**: The LB sends dedicated heartbeats (e.g., a GET request to `/health`) to confirm the server is ready to accept traffic.

### Common Mistakes

- **Single Point of Failure**: If you have only one load balancer, and it fails, your entire system goes down. Use **High Availability (HA)** pairs with a floating IP (like Keepalived) to ensure the LB itself is redundant.
- **SSL Overhead**: L7 balancers often handle SSL decryption (SSL Termination). If not scaled properly, the CPU overhead of encryption can become a bottleneck.
- **Sticky Session Abuse**: Over-reliance on sticky sessions (IP Hash) can lead to uneven traffic distribution if a few 'heavy' users are hashed to the same server.

## Recap

- Load balancers enable **horizontal scaling** by distributing traffic across a pool of servers.
- **Layer 4** is fast and protocol-agnostic; **Layer 7** is smart and content-aware.
- **Health checks** are mandatory to ensure traffic is only sent to functional instances.
- Always ensure your **Load Balancer itself is redundant** to avoid a single point of failure.

### Knowledge Check

Question 1 of 3

Q1Single choice

Which load balancing algorithm is best suited for maintaining session state without a shared cache?

Round Robin

IP Hash

Least Connections

Weighted Round Robin

BackNext

[Previous\\ \\ REST vs GraphQL](https://coursify.hasanraiyan.me/course/system-design-for-software-engineers/rest-vs-graphql) [Next\\ \\ DNS: The Phonebook of the Internet](https://coursify.hasanraiyan.me/course/system-design-for-software-engineers/dns-the-phonebook-of-the-internet)