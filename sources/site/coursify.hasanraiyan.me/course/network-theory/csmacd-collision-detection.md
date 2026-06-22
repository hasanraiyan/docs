# Source: https://coursify.hasanraiyan.me/course/network-theory/csmacd-collision-detection

# CSMA/CD (Collision Detection)

Used traditionally in wired Ethernets, CSMA/CD upgrades CSMA by letting nodes actively monitor the channel during transmission. If a collision is detected, the transmission is aborted immediately, a jam signal is sent, and nodes wait for a dynamically calculated random duration (via Exponential Backoff) before retrying.

### Learning Goals

- The limitation of basic CSMA in wired media.
- CSMA/CD Protocol: The "Listen while talking" mechanism.
- Collision window, minimum frame size restriction, and slot time calculation.
- Exponential Backoff Algorithm: Resolving repeated collisions dynamically.
- Mathematically justify why Ethernet requires a minimum frame size based on the round-trip propagation delay ($2 \\cdot T\_p$).
- Apply the exponential backoff algorithm to determine retransmission delay after successive collisions.

---

In the Data Link Layer, specifically the MAC sublayer, CSMA/CD was designed for classic shared, half-duplex Ethernet where multiple stations contend for one wired medium.[2]() Basic CSMA reduces collisions by listening first, but it cannot eliminate them because propagation delay means two distant stations may both sense an idle channel and begin transmitting almost simultaneously.[2]() CSMA/CD extends CSMA with a crucial idea: stations must keep listening while transmitting so they can detect a collision early, abort, send a jam indication, and retry later using randomized backoff.[2]()

This mechanism is historically central to half-duplex Ethernet, hubs, and shared collision domains, though modern switched full-duplex Ethernet generally does not use collision detection in normal operation.[2]() Understanding CSMA/CD remains essential because it explains why Ethernet adopted a minimum frame size of 64 bytes, why slot time is 512 bit-times in 10/100 Mb/s half-duplex Ethernet, and how binary exponential backoff stabilizes repeated contention.[3]()

## Footnotes

1. [Carrier-sense multiple access with collision detection - Wikipedia](https://en.wikipedia.org/wiki/Carrier-sense_multiple_access_with_collision_detection) - Overview of CSMA/CD, jam signal, slot time, and half-duplex Ethernet behavior. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-1-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-1-3) [↩4](https://coursify.hasanraiyan.me/#user-content-fnref-1-4)
 
2. [\[PDF\] CSMA/CD](https://erg.abdn.ac.uk/users/gorry/course/lan-pages/csma-cd.html) - Explains Ethernet slot time, minimum frame size, late collisions, and retransmission behavior. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-2) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-2-2)
 
3. [\[PDF\] Lecture 19: Ethernet / MAC - Alan Mislove](https://mislove.org/teaching/cs3600/fall14/lectures/lecture19.pdf) - Summarizes Ethernet collision detection, slot time, jam signaling, and exponential backoff. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-3) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-3-2)
 
4. [\[PDF\] 4. Media Access Control - IEEE 802](https://www.ieee802.org/3/as/public/0503/4d0_1_CMP.pdf) - IEEE-oriented description of collision handling, jam, and truncated binary exponential backoff. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-4-2)
 
5. [\[PDF\] Tutorial for CSMA-CD](https://www.site.uottawa.ca/~yongacog/courses/ceg3185/tut7_ceg3185.pdf) - Provides slot-time interpretation and relation to round-trip propagation. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5)
 

#### CSMA/CD and Minimum Frame Length in Ethernet

#### Context in Network Theory

CSMA/CD belongs to shared, half-duplex Ethernet. In switched full-duplex Ethernet, collisions are eliminated by design, but the protocol is still foundational for understanding MAC logic and classic Ethernet engineering.[2]()

## Footnotes

1. [Carrier-sense multiple access with collision detection - Wikipedia](https://en.wikipedia.org/wiki/Carrier-sense_multiple_access_with_collision_detection) - Overview of CSMA/CD, jam signal, slot time, and half-duplex Ethernet behavior. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1)
 
2. [\[PDF\] 4. Media Access Control - IEEE 802](https://www.ieee802.org/3/as/public/0503/4d0_1_CMP.pdf) - IEEE-oriented description of collision handling, jam, and truncated binary exponential backoff. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 

more...

### Why basic CSMA is not enough on wired media

Basic CSMA says: listen first, and if the channel is idle, transmit. The limitation is that the channel state observed at one end of a cable is always slightly outdated at another end because signals travel at finite speed.[2]() Suppose station A starts transmitting; before A's first bit reaches distant station B, station B may still hear silence and begin transmitting as well. The overlap on the cable creates a collision domain, so both frames are corrupted.[2]()

This is why collision _avoidance by sensing alone_ is insufficient on long shared wires. The key engineering improvement is collision detection during transmission itself.[2]() A transmitting station compares what it expects on the line with what it actually senses. If interference is detected, the sender knows another transmitter is active and invokes the collision procedure.[2]()

A useful abstraction is the vulnerable period of length approximately 2Tp2T\_p2Tp​, where TpT\_pTp​ is the one-way end-to-end propagation delay of the collision domain.[2]() If another station starts within this interval, a collision can still occur.

Collision window≈2Tp\\text{Collision window} \\approx 2T\_pCollision window≈2Tp​

The factor of 222 appears because a sender at one extreme must allow enough time for its signal to reach the far end and, in the worst case, for the evidence of a collision to propagate back.[2]()

## Footnotes

1. [\[PDF\] CSMA/CD](https://erg.abdn.ac.uk/users/gorry/course/lan-pages/csma-cd.html) - Explains Ethernet slot time, minimum frame size, late collisions, and retransmission behavior. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-2) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-2-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-2-3)
 
2. [\[PDF\] Tutorial for CSMA-CD](https://www.site.uottawa.ca/~yongacog/courses/ceg3185/tut7_ceg3185.pdf) - Provides slot-time interpretation and relation to round-trip propagation. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-5-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-5-3)
 
3. [Carrier-sense multiple access with collision detection - Wikipedia](https://en.wikipedia.org/wiki/Carrier-sense_multiple_access_with_collision_detection) - Overview of CSMA/CD, jam signal, slot time, and half-duplex Ethernet behavior. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-1-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-1-3)
 
4. [\[PDF\] 4. Media Access Control - IEEE 802](https://www.ieee802.org/3/as/public/0503/4d0_1_CMP.pdf) - IEEE-oriented description of collision handling, jam, and truncated binary exponential backoff. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-4-2)
 
5. [\[PDF\] Lecture 19: Ethernet / MAC - Alan Mislove](https://mislove.org/teaching/cs3600/fall14/lectures/lecture19.pdf) - Summarizes Ethernet collision detection, slot time, jam signaling, and exponential backoff. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-3)
 

### How CSMA/CD Works: Listen While Talking

1. 1
 
 Step 1
 
 Sense the carrier
 
 A station with a frame ready to send first checks whether the medium is busy or idle. If busy, it defers transmission until the medium becomes idle.[2]()
 
 ## Footnotes
 
 1. [Carrier-sense multiple access with collision detection - Wikipedia](https://en.wikipedia.org/wiki/Carrier-sense_multiple_access_with_collision_detection) - Overview of CSMA/CD, jam signal, slot time, and half-duplex Ethernet behavior. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1)
 
 2. [\[PDF\] 4. Media Access Control - IEEE 802](https://www.ieee802.org/3/as/public/0503/4d0_1_CMP.pdf) - IEEE-oriented description of collision handling, jam, and truncated binary exponential backoff. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
 
2. 2
 
 Step 2
 
 Transmit on an idle medium
 
 When the channel appears idle, the station begins sending the frame onto the shared cable.[2]()
 
 ## Footnotes
 
 1. [Carrier-sense multiple access with collision detection - Wikipedia](https://en.wikipedia.org/wiki/Carrier-sense_multiple_access_with_collision_detection) - Overview of CSMA/CD, jam signal, slot time, and half-duplex Ethernet behavior. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1)
 
 2. [\[PDF\] CSMA/CD](https://erg.abdn.ac.uk/users/gorry/course/lan-pages/csma-cd.html) - Explains Ethernet slot time, minimum frame size, late collisions, and retransmission behavior. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-2)
 
 
3. 3
 
 Step 3
 
 Monitor during transmission
 
 Unlike basic CSMA, the station continues monitoring the line while sending. This is the 'listen while talking' behavior that enables rapid collision detection.[2]()
 
 ## Footnotes
 
 1. [Carrier-sense multiple access with collision detection - Wikipedia](https://en.wikipedia.org/wiki/Carrier-sense_multiple_access_with_collision_detection) - Overview of CSMA/CD, jam signal, slot time, and half-duplex Ethernet behavior. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1)
 
 2. [\[PDF\] 4. Media Access Control - IEEE 802](https://www.ieee802.org/3/as/public/0503/4d0_1_CMP.pdf) - IEEE-oriented description of collision handling, jam, and truncated binary exponential backoff. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
 
4. 4
 
 Step 4
 
 Detect the collision
 
 If the observed signal differs from the expected transmit behavior, the sender infers that another station transmitted at nearly the same time and that a collision occurred.[2]()
 
 ## Footnotes
 
 1. [Carrier-sense multiple access with collision detection - Wikipedia](https://en.wikipedia.org/wiki/Carrier-sense_multiple_access_with_collision_detection) - Overview of CSMA/CD, jam signal, slot time, and half-duplex Ethernet behavior. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1)
 
 2. [\[PDF\] 4. Media Access Control - IEEE 802](https://www.ieee802.org/3/as/public/0503/4d0_1_CMP.pdf) - IEEE-oriented description of collision handling, jam, and truncated binary exponential backoff. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
 
5. 5
 
 Step 5
 
 Jam and abort
 
 The sender enforces the collision by transmitting a jam pattern long enough for all involved stations to notice the event, then it terminates the current frame attempt.[2]()
 
 ## Footnotes
 
 1. [Carrier-sense multiple access with collision detection - Wikipedia](https://en.wikipedia.org/wiki/Carrier-sense_multiple_access_with_collision_detection) - Overview of CSMA/CD, jam signal, slot time, and half-duplex Ethernet behavior. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1)
 
 2. [\[PDF\] 4. Media Access Control - IEEE 802](https://www.ieee802.org/3/as/public/0503/4d0_1_CMP.pdf) - IEEE-oriented description of collision handling, jam, and truncated binary exponential backoff. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
 
6. 6
 
 Step 6
 
 Wait using binary exponential backoff
 
 The station chooses a random number of slot times from a contention window that expands after repeated collisions. This reduces the chance that the same stations retransmit together again.[2]()
 
 ## Footnotes
 
 1. [\[PDF\] Lecture 19: Ethernet / MAC - Alan Mislove](https://mislove.org/teaching/cs3600/fall14/lectures/lecture19.pdf) - Summarizes Ethernet collision detection, slot time, jam signaling, and exponential backoff. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-3)
 
 2. [\[PDF\] 4. Media Access Control - IEEE 802](https://www.ieee802.org/3/as/public/0503/4d0_1_CMP.pdf) - IEEE-oriented description of collision handling, jam, and truncated binary exponential backoff. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
 
7. 7
 
 Step 7
 
 Retry or give up
 
 After the backoff interval, the station senses the channel again and retries. Ethernet uses truncated binary exponential backoff and stops after too many failed attempts.[2]()
 
 ## Footnotes
 
 1. [\[PDF\] Lecture 19: Ethernet / MAC - Alan Mislove](https://mislove.org/teaching/cs3600/fall14/lectures/lecture19.pdf) - Summarizes Ethernet collision detection, slot time, jam signaling, and exponential backoff. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-3)
 
 2. [\[PDF\] 4. Media Access Control - IEEE 802](https://www.ieee802.org/3/as/public/0503/4d0_1_CMP.pdf) - IEEE-oriented description of collision handling, jam, and truncated binary exponential backoff. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
 

#### Important Limitation

A collision must be detected while the sender is still transmitting. If the frame ends too early, the sender may falsely assume success. This engineering constraint is the reason for Ethernet's minimum frame size rule.[2]()

## Footnotes

1. [\[PDF\] CSMA/CD](https://erg.abdn.ac.uk/users/gorry/course/lan-pages/csma-cd.html) - Explains Ethernet slot time, minimum frame size, late collisions, and retransmission behavior. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-2)
 
2. [\[PDF\] Tutorial for CSMA-CD](https://www.site.uottawa.ca/~yongacog/courses/ceg3185/tut7_ceg3185.pdf) - Provides slot-time interpretation and relation to round-trip propagation. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5)
 

more...

### Collision window, slot time, and the minimum frame size

In Ethernet, slot time is the time used for collision handling and retransmission scheduling.[2]() For classic 10 Mb/s and 100 Mb/s half-duplex Ethernet, the slot time is 512 bit-times; at 10 Mb/s, this equals 51.2 μs51.2\\,\\mu s51.2μs.[2]() This value is not arbitrary: it is chosen so that a station can still be transmitting when a worst-case collision returns from the farthest point in the permitted collision domain.[2]()

Let:

- RRR = link bit rate in bits/s
- TpT\_pTp​ = one-way maximum propagation delay across the collision domain
- Lmin⁡L\_{\\min}Lmin​ = minimum frame length in bits

For collision detection to work correctly, the sender's transmission time must be at least the round-trip propagation delay:

Lmin⁡R≥2Tp\\frac{L\_{\\min}}{R} \\ge 2T\_pRLmin​​≥2Tp​

Multiplying both sides by RRR gives the fundamental design inequality:

Lmin⁡≥2RTpL\_{\\min} \\ge 2RT\_pLmin​≥2RTp​

This is the mathematical justification for Ethernet's minimum frame size requirement.[3]() If a frame were shorter than 2RTp2RT\_p2RTp​ bits, a far-end collision could occur and the sender could finish transmission _before_ the collision signal returned, making detection impossible.[2]()

For classic Ethernet, the standardized minimum frame length is 64 bytes, or:

Lmin⁡\=64×8\=512 bitsL\_{\\min} = 64 \\times 8 = 512 \\text{ bits}Lmin​\=64×8\=512 bits

Hence the transmission time of the smallest legal frame equals one slot time:

Tslot\=512RT\_{\\text{slot}} = \\frac{512}{R}Tslot​\=R512​

Examples:

| Ethernet Rate | Slot Time in Bit-Times | Slot Time in Seconds |
| --- | --- | --- |
| 101010 Mb/s | 512512512 | 51.2 μs51.2\\,\\mu s51.2μs |
| 100100100 Mb/s | 512512512 | 5.12 μs5.12\\,\\mu s5.12μs |

A collision detected after the first slot time is called a late collision and generally indicates a misconfigured or faulty network, such as excessive cable distance or timing problems.

## Footnotes

1. [\[PDF\] Lecture 19: Ethernet / MAC - Alan Mislove](https://mislove.org/teaching/cs3600/fall14/lectures/lecture19.pdf) - Summarizes Ethernet collision detection, slot time, jam signaling, and exponential backoff. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-3) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-3-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-3-3)
 
2. [\[PDF\] 4. Media Access Control - IEEE 802](https://www.ieee802.org/3/as/public/0503/4d0_1_CMP.pdf) - IEEE-oriented description of collision handling, jam, and truncated binary exponential backoff. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
3. [\[PDF\] CSMA/CD](https://erg.abdn.ac.uk/users/gorry/course/lan-pages/csma-cd.html) - Explains Ethernet slot time, minimum frame size, late collisions, and retransmission behavior. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-2) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-2-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-2-3) [↩4](https://coursify.hasanraiyan.me/#user-content-fnref-2-4) [↩5](https://coursify.hasanraiyan.me/#user-content-fnref-2-5)
 
4. [\[PDF\] Tutorial for CSMA-CD](https://www.site.uottawa.ca/~yongacog/courses/ceg3185/tut7_ceg3185.pdf) - Provides slot-time interpretation and relation to round-trip propagation. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-5-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-5-3)
 

### 

Ethernet Slot Time by Link Rate

For half-duplex Ethernet, 10 and 100 Mb/s retain a slot time of 512 bit-times; the duration shrinks as bit rate rises.

### Mathematical justification of the 2Tp2T\_p2Tp​ rule

Consider two stations A and B at opposite ends of the maximum allowed collision domain.[2]()

1. A begins transmission at time t\=0t=0t\=0.
2. A's first bit reaches B after one-way propagation delay TpT\_pTp​.
3. In the worst case, B starts transmitting just before A's signal arrives, so B still believes the medium is idle.[2]()
4. The collision effect must then travel back toward A, taking nearly another TpT\_pTp​.
5. Therefore A may not detect the collision until almost 2Tp2T\_p2Tp​ after starting.[2]()

So if A is to detect the collision before finishing transmission, the frame transmission time TfT\_fTf​ must satisfy:

Tf≥2TpT\_f \\ge 2T\_pTf​≥2Tp​

Since Tf\=LRT\_f = \\frac{L}{R}Tf​\=RL​:

LR≥2Tp⇒L≥2RTp\\frac{L}{R} \\ge 2T\_p \\quad \\Rightarrow \\quad L \\ge 2RT\_pRL​≥2Tp​⇒L≥2RTp​

This simple inequality connects physical distance, propagation speed, and MAC-layer frame design.[2]()

If propagation speed is approximately v≈2×108 m/sv \\approx 2 \\times 10^8 \\text{ m/s}v≈2×108 m/s, then for cable length ddd:

Tp≈dvT\_p \\approx \\frac{d}{v}Tp​≈vd​

Substituting into the minimum-frame inequality:

Lmin⁡≥2RdvL\_{\\min} \\ge 2R\\frac{d}{v}Lmin​≥2Rvd​

or equivalently:

d≤Lmin⁡v2Rd \\le \\frac{L\_{\\min}v}{2R}d≤2RLmin​v​

Thus, fixing Lmin⁡\=512L\_{\\min}=512Lmin​\=512 bits constrains the maximum collision-domain diameter for a given bit rate.[2]() This is why faster shared Ethernet requires tighter diameter limits or altered slot-time engineering.

## Footnotes

1. [\[PDF\] CSMA/CD](https://erg.abdn.ac.uk/users/gorry/course/lan-pages/csma-cd.html) - Explains Ethernet slot time, minimum frame size, late collisions, and retransmission behavior. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-2) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-2-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-2-3) [↩4](https://coursify.hasanraiyan.me/#user-content-fnref-2-4)
 
2. [\[PDF\] Tutorial for CSMA-CD](https://www.site.uottawa.ca/~yongacog/courses/ceg3185/tut7_ceg3185.pdf) - Provides slot-time interpretation and relation to round-trip propagation. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-5-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-5-3) [↩4](https://coursify.hasanraiyan.me/#user-content-fnref-5-4) [↩5](https://coursify.hasanraiyan.me/#user-content-fnref-5-5)
 
3. [\[PDF\] Lecture 19: Ethernet / MAC - Alan Mislove](https://mislove.org/teaching/cs3600/fall14/lectures/lecture19.pdf) - Summarizes Ethernet collision detection, slot time, jam signaling, and exponential backoff. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-3) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-3-2)
 

### Key Concepts and Edge Cases

What exactly is the collision window?

Why is the minimum Ethernet frame 64 bytes?

What is a late collision?

Does CSMA/CD matter in modern switched networks?

### Binary exponential backoff: resolving repeated collisions

After a collision, immediate retransmission would likely cause another collision, especially if the same stations are contending.[2]() Ethernet therefore uses binary exponential backoff to spread retransmission attempts over time.

If a frame has experienced iii collisions, the station chooses a random integer KKK from:

K∈{0,1,…,2i−1}K \\in \\{0,1,\\dots,2^i - 1\\}K∈{0,1,…,2i−1}

for early collisions, with Ethernet applying truncation so the exponent does not grow indefinitely.[2]() The retransmission delay is then:

Tbackoff\=K⋅TslotT\_{\\text{backoff}} = K \\cdot T\_{\\text{slot}}Tbackoff​\=K⋅Tslot​

where Tslot\=512T\_{\\text{slot}} = 512Tslot​\=512 bit-times for 10/100 Mb/s half-duplex Ethernet.[2]()

So:

- After the 1st collision: K∈{0,1}K \\in \\{0,1\\}K∈{0,1}
- After the 2nd collision: K∈{0,1,2,3}K \\in \\{0,1,2,3\\}K∈{0,1,2,3}
- After the 3rd collision: K∈{0,…,7}K \\in \\{0,\\dots,7\\}K∈{0,…,7}

The window doubles each time, reducing the probability that the same stations pick identical retry times again.[2]() This adaptive behavior is especially effective under bursty contention because it enlarges the contention window only when repeated collisions suggest high load.

The expected backoff after iii collisions, assuming uniform selection over {0,…,2i−1}\\{0,\\dots,2^i-1\\}{0,…,2i−1}, is:

E\[K\]\=2i−12\\mathbb{E}\[K\] = \\frac{2^i - 1}{2}E\[K\]\=22i−1​

Hence the expected retransmission delay is:

E\[Tbackoff\]\=2i−12 Tslot\\mathbb{E}\[T\_{\\text{backoff}}\] = \\frac{2^i - 1}{2} \\, T\_{\\text{slot}}E\[Tbackoff​\]\=22i−1​Tslot​

This shows mathematically why waiting grows rapidly with repeated collisions.

## Footnotes

1. [\[PDF\] Lecture 19: Ethernet / MAC - Alan Mislove](https://mislove.org/teaching/cs3600/fall14/lectures/lecture19.pdf) - Summarizes Ethernet collision detection, slot time, jam signaling, and exponential backoff. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-3) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-3-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-3-3) [↩4](https://coursify.hasanraiyan.me/#user-content-fnref-3-4)
 
2. [\[PDF\] 4. Media Access Control - IEEE 802](https://www.ieee802.org/3/as/public/0503/4d0_1_CMP.pdf) - IEEE-oriented description of collision handling, jam, and truncated binary exponential backoff. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-4-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-4-3)
 
3. [\[PDF\] Tutorial for CSMA-CD](https://www.site.uottawa.ca/~yongacog/courses/ceg3185/tut7_ceg3185.pdf) - Provides slot-time interpretation and relation to round-trip propagation. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5)
 

### Applying the Exponential Backoff Algorithm

1. 1
 
 Step 1
 
 Count collisions for the same frame
 
 Let iii be the number of collisions already experienced by the current frame. Ethernet uses this count to size the contention window.[2]()
 
 ## Footnotes
 
 1. [\[PDF\] Lecture 19: Ethernet / MAC - Alan Mislove](https://mislove.org/teaching/cs3600/fall14/lectures/lecture19.pdf) - Summarizes Ethernet collision detection, slot time, jam signaling, and exponential backoff. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-3)
 
 2. [\[PDF\] 4. Media Access Control - IEEE 802](https://www.ieee802.org/3/as/public/0503/4d0_1_CMP.pdf) - IEEE-oriented description of collision handling, jam, and truncated binary exponential backoff. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
 
2. 2
 
 Step 2
 
 Compute the backoff range
 
 Choose the random slot count from 000 through 2i−12^i - 12i−1 for early retries, subject to Ethernet's truncation rules.[2]()
 
 ## Footnotes
 
 1. [\[PDF\] Lecture 19: Ethernet / MAC - Alan Mislove](https://mislove.org/teaching/cs3600/fall14/lectures/lecture19.pdf) - Summarizes Ethernet collision detection, slot time, jam signaling, and exponential backoff. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-3)
 
 2. [\[PDF\] 4. Media Access Control - IEEE 802](https://www.ieee802.org/3/as/public/0503/4d0_1_CMP.pdf) - IEEE-oriented description of collision handling, jam, and truncated binary exponential backoff. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
 
3. 3
 
 Step 3
 
 Pick a random integer
 
 Select one value KKK uniformly from the valid range. Different stations are unlikely to choose the same value repeatedly.
 
 ## Footnotes
 
 1. [\[PDF\] Lecture 19: Ethernet / MAC - Alan Mislove](https://mislove.org/teaching/cs3600/fall14/lectures/lecture19.pdf) - Summarizes Ethernet collision detection, slot time, jam signaling, and exponential backoff. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-3)
 
 
4. 4
 
 Step 4
 
 Convert slots to time
 
 Multiply by slot time: Tbackoff\=K⋅TslotT\_{backoff}=K \\cdot T\_{slot}Tbackoff​\=K⋅Tslot​. At 101010 Mb/s, Tslot\=51.2 μsT\_{slot}=51.2\\,\\mu sTslot​\=51.2μs; at 100100100 Mb/s, Tslot\=5.12 μsT\_{slot}=5.12\\,\\mu sTslot​\=5.12μs.[2]()
 
 ## Footnotes
 
 1. [\[PDF\] CSMA/CD](https://erg.abdn.ac.uk/users/gorry/course/lan-pages/csma-cd.html) - Explains Ethernet slot time, minimum frame size, late collisions, and retransmission behavior. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-2)
 
 2. [\[PDF\] Tutorial for CSMA-CD](https://www.site.uottawa.ca/~yongacog/courses/ceg3185/tut7_ceg3185.pdf) - Provides slot-time interpretation and relation to round-trip propagation. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5)
 
 
5. 5
 
 Step 5
 
 Retry after waiting
 
 After the selected delay, the station senses the channel again. If idle, it retransmits; otherwise it continues deferring under carrier sense rules.[2]()
 
 ## Footnotes
 
 1. [Carrier-sense multiple access with collision detection - Wikipedia](https://en.wikipedia.org/wiki/Carrier-sense_multiple_access_with_collision_detection) - Overview of CSMA/CD, jam signal, slot time, and half-duplex Ethernet behavior. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1)
 
 2. [\[PDF\] 4. Media Access Control - IEEE 802](https://www.ieee802.org/3/as/public/0503/4d0_1_CMP.pdf) - IEEE-oriented description of collision handling, jam, and truncated binary exponential backoff. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
 
6. 6
 
 Step 6
 
 Abort after too many attempts
 
 Ethernet specifies a finite retry limit. If too many collisions occur for the same frame, the transmission is reported as failed rather than retried forever.[2]()
 
 ## Footnotes
 
 1. [\[PDF\] Lecture 19: Ethernet / MAC - Alan Mislove](https://mislove.org/teaching/cs3600/fall14/lectures/lecture19.pdf) - Summarizes Ethernet collision detection, slot time, jam signaling, and exponential backoff. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-3)
 
 2. [\[PDF\] 4. Media Access Control - IEEE 802](https://www.ieee802.org/3/as/public/0503/4d0_1_CMP.pdf) - IEEE-oriented description of collision handling, jam, and truncated binary exponential backoff. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
 

Formula Summary

Worked ExampleDistance Example

Minimum-frame condition: Lmin⁡R≥2Tp\\frac{L\_{\\min}}{R} \\ge 2T\_pRLmin​​≥2Tp​

Equivalent form: Lmin⁡≥2RTpL\_{\\min} \\ge 2RT\_pLmin​≥2RTp​

Slot time: Tslot\=512RT\_{slot}=\\frac{512}{R}Tslot​\=R512​

Backoff delay after iii collisions: Tbackoff\=K Tslot,K∈{0,…,2i−1}T\_{backoff}=K\\,T\_{slot}, \\quad K\\in\\{0,\\dots,2^i-1\\}Tbackoff​\=KTslot​,K∈{0,…,2i−1}

Expected slot count: E\[K\]\=2i−12\\mathbb{E}\[K\]=\\frac{2^i-1}{2}E\[K\]\=22i−1​

### 

CSMA/CD Transmission Lifecycle

#### Carrier Sensing

Stage 1

A station listens to determine whether the shared medium is currently busy or idle."

## Footnotes

1. [Carrier-sense multiple access with collision detection - Wikipedia](https://en.wikipedia.org/wiki/Carrier-sense_multiple_access_with_collision_detection) - Overview of CSMA/CD, jam signal, slot time, and half-duplex Ethernet behavior. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1)
 

#### Frame Transmission

Stage 2

If idle, the station transmits but continues monitoring the line while sending.[2]()"

## Footnotes

1. [Carrier-sense multiple access with collision detection - Wikipedia](https://en.wikipedia.org/wiki/Carrier-sense_multiple_access_with_collision_detection) - Overview of CSMA/CD, jam signal, slot time, and half-duplex Ethernet behavior. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1)
 
2. [\[PDF\] 4. Media Access Control - IEEE 802](https://www.ieee802.org/3/as/public/0503/4d0_1_CMP.pdf) - IEEE-oriented description of collision handling, jam, and truncated binary exponential backoff. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 

#### Collision Detection

Stage 3

A mismatch or interference on the medium indicates overlapping transmissions.[2]()"

## Footnotes

1. [Carrier-sense multiple access with collision detection - Wikipedia](https://en.wikipedia.org/wiki/Carrier-sense_multiple_access_with_collision_detection) - Overview of CSMA/CD, jam signal, slot time, and half-duplex Ethernet behavior. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1)
 
2. [\[PDF\] 4. Media Access Control - IEEE 802](https://www.ieee802.org/3/as/public/0503/4d0_1_CMP.pdf) - IEEE-oriented description of collision handling, jam, and truncated binary exponential backoff. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 

#### Jam and Abort

Stage 4

The sender enforces the collision with a jam indication so all participants recognize the corrupted event.[2]()"

## Footnotes

1. [Carrier-sense multiple access with collision detection - Wikipedia](https://en.wikipedia.org/wiki/Carrier-sense_multiple_access_with_collision_detection) - Overview of CSMA/CD, jam signal, slot time, and half-duplex Ethernet behavior. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1)
 
2. [\[PDF\] 4. Media Access Control - IEEE 802](https://www.ieee802.org/3/as/public/0503/4d0_1_CMP.pdf) - IEEE-oriented description of collision handling, jam, and truncated binary exponential backoff. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 

#### Binary Exponential Backoff

Stage 5

The station waits a random number of slot times selected from an expanding contention window.[2]()"

## Footnotes

1. [\[PDF\] Lecture 19: Ethernet / MAC - Alan Mislove](https://mislove.org/teaching/cs3600/fall14/lectures/lecture19.pdf) - Summarizes Ethernet collision detection, slot time, jam signaling, and exponential backoff. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-3)
 
2. [\[PDF\] 4. Media Access Control - IEEE 802](https://www.ieee802.org/3/as/public/0503/4d0_1_CMP.pdf) - IEEE-oriented description of collision handling, jam, and truncated binary exponential backoff. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 

#### Retransmission or Failure

Stage 6

The frame is retried until success or until the retry limit is reached.[2]()"

## Footnotes

1. [\[PDF\] Lecture 19: Ethernet / MAC - Alan Mislove](https://mislove.org/teaching/cs3600/fall14/lectures/lecture19.pdf) - Summarizes Ethernet collision detection, slot time, jam signaling, and exponential backoff. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-3)
 
2. [\[PDF\] 4. Media Access Control - IEEE 802](https://www.ieee802.org/3/as/public/0503/4d0_1_CMP.pdf) - IEEE-oriented description of collision handling, jam, and truncated binary exponential backoff. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 

#### Exam Strategy

When asked why Ethernet needs a minimum frame size, start from the worst-case collision path: the sender must still be transmitting after a round trip of approximately 2Tp2T\_p2Tp​, so Lmin≥2RTpL\_{min} \\ge 2RT\_pLmin​≥2RTp​.[2]()

## Footnotes

1. [\[PDF\] CSMA/CD](https://erg.abdn.ac.uk/users/gorry/course/lan-pages/csma-cd.html) - Explains Ethernet slot time, minimum frame size, late collisions, and retransmission behavior. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-2)
 
2. [\[PDF\] Tutorial for CSMA-CD](https://www.site.uottawa.ca/~yongacog/courses/ceg3185/tut7_ceg3185.pdf) - Provides slot-time interpretation and relation to round-trip propagation. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5)
 

more...

### Practical interpretation for Network Theory

From a theoretical perspective, CSMA/CD links the physical properties of a medium to MAC-layer correctness.[2]() The protocol is not merely a rule set for contention; it is an example of cross-layer constraint where propagation delay, transmission rate, and frame format must be jointly engineered.[2]()

The most important takeaways for the Data Link Layer and Medium Access Sub Layer are:

1. Basic CSMA lowers collision probability but cannot prevent collisions on a finite-speed shared medium.[2]()
2. CSMA/CD solves this by requiring stations to detect collisions while transmitting.[2]()
3. The legal collision window is governed by approximately 2Tp2T\_p2Tp​, motivating Ethernet slot time.[2]()
4. The minimum frame size follows directly from the requirement Lmin⁡R≥2Tp\\frac{L\_{\\min}}{R}\\ge 2T\_pRLmin​​≥2Tp​.[2]()
5. Repeated collisions are resolved dynamically by truncated binary exponential backoff.[2]()

These ideas remain pedagogically significant even though switched full-duplex Ethernet largely removed shared-medium collisions from everyday practice.[2]()

## Footnotes

1. [\[PDF\] CSMA/CD](https://erg.abdn.ac.uk/users/gorry/course/lan-pages/csma-cd.html) - Explains Ethernet slot time, minimum frame size, late collisions, and retransmission behavior. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-2) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-2-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-2-3) [↩4](https://coursify.hasanraiyan.me/#user-content-fnref-2-4)
 
2. [\[PDF\] 4. Media Access Control - IEEE 802](https://www.ieee802.org/3/as/public/0503/4d0_1_CMP.pdf) - IEEE-oriented description of collision handling, jam, and truncated binary exponential backoff. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-4-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-4-3) [↩4](https://coursify.hasanraiyan.me/#user-content-fnref-4-4)
 
3. [\[PDF\] Lecture 19: Ethernet / MAC - Alan Mislove](https://mislove.org/teaching/cs3600/fall14/lectures/lecture19.pdf) - Summarizes Ethernet collision detection, slot time, jam signaling, and exponential backoff. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-3) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-3-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-3-3)
 
4. [Carrier-sense multiple access with collision detection - Wikipedia](https://en.wikipedia.org/wiki/Carrier-sense_multiple_access_with_collision_detection) - Overview of CSMA/CD, jam signal, slot time, and half-duplex Ethernet behavior. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-1-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-1-3)
 
5. [\[PDF\] Tutorial for CSMA-CD](https://www.site.uottawa.ca/~yongacog/courses/ceg3185/tut7_ceg3185.pdf) - Provides slot-time interpretation and relation to round-trip propagation. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-5-2)
 

### Knowledge Check

Question 1 of 5

Q1Single choice

Why can collisions still occur in basic CSMA on a wired medium even if all stations listen before transmitting?

Because propagation delay can make two distant stations both perceive the medium as idle

Because Ethernet does not use addresses

Because CRC always fails on short frames

Because switches intentionally create collisions

BackNext

[Previous\\ \\ Random Access Protocols (ALOHA & CSMA)](https://coursify.hasanraiyan.me/course/network-theory/random-access-protocols-aloha-csma) [Next\\ \\ CSMA/CA Collision Avoidance and Medium Access Control in Wireless Networks](https://coursify.hasanraiyan.me/course/network-theory/csmaca-collision-avoidance-and-medium-access-control-in-wireless-networks)