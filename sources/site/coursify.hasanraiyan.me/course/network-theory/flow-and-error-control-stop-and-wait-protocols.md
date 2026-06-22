# Source: https://coursify.hasanraiyan.me/course/network-theory/flow-and-error-control-stop-and-wait-protocols

# Flow and Error Control – Stop-and-Wait Protocols

Flow control prevents a fast transmitter from overwhelming a slow receiver. Stop-and-Wait forces the sender to halt and wait for an explicit acknowledgment (ACK) after every single frame. The ARQ version introduces timers and sequence numbers to handle packet loss automatically, though channel utilization remains low.

### Learning Goals

- Need for Flow Control (matching sender speed with receiver capacity).
- Connectionless vs. Connection-oriented protocols at the Data Link Layer.
- Stop-and-Wait Protocol: Working mechanism, sequence numbers, and efficiency analysis.
- Stop-and-Wait ARQ (Automatic Repeat Request): Handling lost frames, lost ACKs, and delayed ACKs using timers.
- Explain the performance bottlenecks of the basic Stop-and-Wait protocol over high-latency channels.
- Diagram how Stop-and-Wait ARQ recovers gracefully from dropped frames or acknowledgments using timeouts.

---

In the Data Link Layer of Network Theory, flow control is necessary because a fast sender can inject frames more quickly than a slow receiver can process, buffer, and deliver them upward.[2]() The Stop-and-Wait protocol is the simplest practical response to this mismatch: the sender transmits one frame, stops, and waits for an acknowledgment before sending the next.[2]() In a noiseless setting, this provides basic pacing; in a noisy setting, it evolves into Stop-and-Wait ARQ, which adds reliability through acknowledgments, timers, and retransmissions.[2]()

Within the data link layer, protocols may be connectionless or connection-oriented. In connectionless service, each frame is treated independently and often without ordering guarantees beyond the local link behavior; this style is common in many LANs. In connection-oriented service, a logical relationship exists among frames, they are typically numbered, and ordered transfer with acknowledgments becomes meaningful.[2]() Stop-and-Wait fits naturally into the connection-oriented model because acknowledgments and sequence numbers create state on both sender and receiver.[2]()

Conceptually, Stop-and-Wait can also be viewed as a sliding window protocol with sender window size W\=1W=1W\=1 and receiver window size W\=1W=1W\=1.[2]() This extreme simplicity makes it easy to implement and reason about, but its chief limitation is poor channel utilization when the propagation delay is large compared with the transmission delay.[2]()

## Footnotes

1. [Data-link Control & Protocols](https://www.tutorialspoint.com/data_communication_computer_network/data_link_control_and_protocols.htm) - Overview of data link layer flow control and stop-and-wait basics. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-1-2)
 
2. [Data Link Control Protocols - sandilands.info](https://sandilands.info/sgordon/teaching/its323y08s1/protected/ITS323Y08S1L08-DataLinkControlProtocols.pdf) - Lecture notes giving stop-and-wait throughput and efficiency analysis. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-2) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-2-2)
 
3. [Simplex Stop and Wait Protocol](https://www.southampton.ac.uk/~sqc/EL336/CNL-5.pdf) - University lecture notes relating stop-and-wait to sliding windows and utilization on LAN and satellite links. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-3) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-3-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-3-3)
 
4. [The Data Link Layer: ARQ Protocols - MIT](https://web.mit.edu/modiano/www/6.263/lec3-4.pdf) - Detailed explanation of stop-and-wait ARQ, timeouts, and sequence numbers. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
5. [III. Link Layer ARQ Protocols - CMU](https://mews.sv.cmu.edu/courses/565-w08/files/topic03notes.pdf) - Notes on stop-and-wait ARQ behavior under losses, delays, and retransmissions. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5)
 
6. [UNIT 2 INTRODUCTION TO DATALINK LAYER](http://www.gpcet.ac.in/wp-content/uploads/2018/08/UNIT-I-II-III-CN-R13-JNTUAnew-51-74.pdf) - Educational notes distinguishing connectionless and connection-oriented data link protocols. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-6) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-6-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-6-3)
 
7. [Data Link Layer Protocols](https://web.cs.wpi.edu/~cs513/s07/week3-dllprot.pdf) - Lecture material linking stop-and-wait to sliding-window operation with window size 111. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-7) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-7-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-7-3)
 

#### Stop-and-Wait ARQ Protocol

#### Why Flow Control Exists

Even on an error-free link, reliability alone is not enough. If the receiver processes frames slower than the sender emits them, buffer overflow and frame loss can occur unless pacing is enforced.[2]()

## Footnotes

1. [Data-link Control & Protocols](https://www.tutorialspoint.com/data_communication_computer_network/data_link_control_and_protocols.htm) - Overview of data link layer flow control and stop-and-wait basics. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1)
 
2. [Data Link Control Protocols - sandilands.info](https://sandilands.info/sgordon/teaching/its323y08s1/protected/ITS323Y08S1L08-DataLinkControlProtocols.pdf) - Lecture notes giving stop-and-wait throughput and efficiency analysis. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-2)
 

more...

### Connectionless vs. Connection-Oriented Data Link Behavior

At the data link layer, a connectionless protocol sends frames as independent units. There is no logical setup phase, no per-exchange state tying one frame to the next, and usually no requirement that frames be numbered for in-order delivery. This design is efficient for many LAN scenarios where the medium is short, error rates are low, and higher layers can handle recovery if necessary.

A connection-oriented protocol, by contrast, establishes logical state before useful transfer, sends frames as part of an ordered exchange, and often ends with a teardown or completion stage. Since the sender and receiver maintain state, mechanisms such as sequence numbers, acknowledgments, and retransmission timers become meaningful and correct.[2]() Stop-and-Wait and Stop-and-Wait ARQ belong to this stateful family because the sender must know whether the current outstanding frame has been accepted.[2]()

| Feature | Connectionless DLL | Connection-Oriented DLL |
| --- | --- | --- |
| Relationship between frames | Independent | Part of one logical exchange |
| Setup/teardown | Usually absent | Usually present or implied by state |
| Ordering concern | Limited | Important |
| Sequence numbers | Often unnecessary | Common and useful[2]() |
| Typical use | Many LAN links | Point-to-point, some wireless/WAN contexts |
| Fit for Stop-and-Wait | Weak | Strong[2]() |

## Footnotes

1. [UNIT 2 INTRODUCTION TO DATALINK LAYER](http://www.gpcet.ac.in/wp-content/uploads/2018/08/UNIT-I-II-III-CN-R13-JNTUAnew-51-74.pdf) - Educational notes distinguishing connectionless and connection-oriented data link protocols. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-6) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-6-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-6-3) [↩4](https://coursify.hasanraiyan.me/#user-content-fnref-6-4) [↩5](https://coursify.hasanraiyan.me/#user-content-fnref-6-5) [↩6](https://coursify.hasanraiyan.me/#user-content-fnref-6-6) [↩7](https://coursify.hasanraiyan.me/#user-content-fnref-6-7) [↩8](https://coursify.hasanraiyan.me/#user-content-fnref-6-8) [↩9](https://coursify.hasanraiyan.me/#user-content-fnref-6-9) [↩10](https://coursify.hasanraiyan.me/#user-content-fnref-6-10) [↩11](https://coursify.hasanraiyan.me/#user-content-fnref-6-11) [↩12](https://coursify.hasanraiyan.me/#user-content-fnref-6-12) [↩13](https://coursify.hasanraiyan.me/#user-content-fnref-6-13)
 
2. [The Data Link Layer: ARQ Protocols - MIT](https://web.mit.edu/modiano/www/6.263/lec3-4.pdf) - Detailed explanation of stop-and-wait ARQ, timeouts, and sequence numbers. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-4-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-4-3)
 
3. [Data Link Layer Protocols](https://web.cs.wpi.edu/~cs513/s07/week3-dllprot.pdf) - Lecture material linking stop-and-wait to sliding-window operation with window size 111. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-7) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-7-2)
 
4. [Data-link Control & Protocols](https://www.tutorialspoint.com/data_communication_computer_network/data_link_control_and_protocols.htm) - Overview of data link layer flow control and stop-and-wait basics. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1)
 

### Basic Stop-and-Wait Protocol Operation

1. 1
 
 Step 1
 
 Transmit one frame
 
 The sender takes one packet from the network layer, encapsulates it into a frame, and sends exactly one outstanding frame onto the link.[2]()
 
 ## Footnotes
 
 1. [Data-link Control & Protocols](https://www.tutorialspoint.com/data_communication_computer_network/data_link_control_and_protocols.htm) - Overview of data link layer flow control and stop-and-wait basics. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1)
 
 2. [Simplex Stop and Wait Protocol](https://www.southampton.ac.uk/~sqc/EL336/CNL-5.pdf) - University lecture notes relating stop-and-wait to sliding windows and utilization on LAN and satellite links. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-3)
 
 
2. 2
 
 Step 2
 
 Pause after transmission
 
 After sending, the sender does not inject additional data. This enforced idle period is what provides flow control.[2]()
 
 ## Footnotes
 
 1. [Data-link Control & Protocols](https://www.tutorialspoint.com/data_communication_computer_network/data_link_control_and_protocols.htm) - Overview of data link layer flow control and stop-and-wait basics. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1)
 
 2. [Data Link Control Protocols - sandilands.info](https://sandilands.info/sgordon/teaching/its323y08s1/protected/ITS323Y08S1L08-DataLinkControlProtocols.pdf) - Lecture notes giving stop-and-wait throughput and efficiency analysis. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-2)
 
 
3. 3
 
 Step 3
 
 Receiver processes the frame
 
 The receiver accepts the frame, removes the payload, and forwards it upward if the frame is valid and expected.[2]()
 
 ## Footnotes
 
 1. [Data-link Control & Protocols](https://www.tutorialspoint.com/data_communication_computer_network/data_link_control_and_protocols.htm) - Overview of data link layer flow control and stop-and-wait basics. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1)
 
 2. [The Data Link Layer: ARQ Protocols - MIT](https://web.mit.edu/modiano/www/6.263/lec3-4.pdf) - Detailed explanation of stop-and-wait ARQ, timeouts, and sequence numbers. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
 
4. 4
 
 Step 4
 
 Receiver returns acknowledgment
 
 An acknowledgment indicates successful receipt and permission for the next frame.[2]()
 
 ## Footnotes
 
 1. [Data-link Control & Protocols](https://www.tutorialspoint.com/data_communication_computer_network/data_link_control_and_protocols.htm) - Overview of data link layer flow control and stop-and-wait basics. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1)
 
 2. [The Data Link Layer: ARQ Protocols - MIT](https://web.mit.edu/modiano/www/6.263/lec3-4.pdf) - Detailed explanation of stop-and-wait ARQ, timeouts, and sequence numbers. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
 
5. 5
 
 Step 5
 
 Sender resumes only after ACK
 
 Once the acknowledgment arrives, the sender is allowed to transmit the next frame.[2]()
 
 ## Footnotes
 
 1. [Data-link Control & Protocols](https://www.tutorialspoint.com/data_communication_computer_network/data_link_control_and_protocols.htm) - Overview of data link layer flow control and stop-and-wait basics. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1)
 
 2. [Simplex Stop and Wait Protocol](https://www.southampton.ac.uk/~sqc/EL336/CNL-5.pdf) - University lecture notes relating stop-and-wait to sliding windows and utilization on LAN and satellite links. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-3)
 
 
6. 6
 
 Step 6
 
 Repeat for every frame
 
 Because only one frame may remain unacknowledged at any time, the protocol is simple but often underutilizes the link.[2]()
 
 ## Footnotes
 
 1. [Data Link Control Protocols - sandilands.info](https://sandilands.info/sgordon/teaching/its323y08s1/protected/ITS323Y08S1L08-DataLinkControlProtocols.pdf) - Lecture notes giving stop-and-wait throughput and efficiency analysis. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-2)
 
 2. [Simplex Stop and Wait Protocol](https://www.southampton.ac.uk/~sqc/EL336/CNL-5.pdf) - University lecture notes relating stop-and-wait to sliding windows and utilization on LAN and satellite links. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-3)
 
 

### Working Mechanism, Sequence Numbers, and Correctness

In the basic noiseless form, the acknowledgment merely signals “ready for the next frame.” However, once errors, loss, or delayed acknowledgments are possible, simple acknowledgments are insufficient.[2]() The central problem is ambiguity: if a sender times out and retransmits, the receiver must know whether the arriving frame is a new frame or a duplicate of an older one.[2]()

This is why Stop-and-Wait ARQ uses a 1-bit sequence space, commonly 000 and 111.[2]() Since at most one frame can be outstanding, the receiver only needs to distinguish between “the frame I currently expect” and “a duplicate of the one already accepted.” If the sender transmits frame with sequence number 000, then after correct delivery the receiver sends an acknowledgment indicating it next expects 111; after accepting frame 111, it next expects 000 again.[2]()

This alternating-bit behavior is enough because the sender cannot legally send frame 111 until frame 000 is acknowledged, and vice versa.[2]() Thus, one bit of numbering prevents duplicate delivery while keeping implementation minimal.

## Footnotes

1. [The Data Link Layer: ARQ Protocols - MIT](https://web.mit.edu/modiano/www/6.263/lec3-4.pdf) - Detailed explanation of stop-and-wait ARQ, timeouts, and sequence numbers. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-4-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-4-3) [↩4](https://coursify.hasanraiyan.me/#user-content-fnref-4-4) [↩5](https://coursify.hasanraiyan.me/#user-content-fnref-4-5) [↩6](https://coursify.hasanraiyan.me/#user-content-fnref-4-6)
 
2. [III. Link Layer ARQ Protocols - CMU](https://mews.sv.cmu.edu/courses/565-w08/files/topic03notes.pdf) - Notes on stop-and-wait ARQ behavior under losses, delays, and retransmissions. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-5-2)
 
3. [Data Link Layer Protocols](https://web.cs.wpi.edu/~cs513/s07/week3-dllprot.pdf) - Lecture material linking stop-and-wait to sliding-window operation with window size 111. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-7) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-7-2)
 
4. [Simplex Stop and Wait Protocol](https://www.southampton.ac.uk/~sqc/EL336/CNL-5.pdf) - University lecture notes relating stop-and-wait to sliding windows and utilization on LAN and satellite links. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-3)
 

#### Key Insight

Stop-and-Wait ARQ does not need large sequence spaces. Because only one frame is outstanding, a 1-bit alternating sequence number is sufficient to detect duplicates.[2]()

## Footnotes

1. [The Data Link Layer: ARQ Protocols - MIT](https://web.mit.edu/modiano/www/6.263/lec3-4.pdf) - Detailed explanation of stop-and-wait ARQ, timeouts, and sequence numbers. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
2. [Data Link Layer Protocols](https://web.cs.wpi.edu/~cs513/s07/week3-dllprot.pdf) - Lecture material linking stop-and-wait to sliding-window operation with window size 111. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-7)
 

more...

### Efficiency Analysis and the High-Latency Bottleneck

The principal weakness of Stop-and-Wait is not correctness but efficiency.[2]() During each cycle, only one frame transmission interval carries useful data, while the sender then idles during forward propagation, acknowledgment return, and reverse propagation. Under the standard simplifying assumptions that ACK transmission time and processing time are negligible, total cycle time is:

Tcycle\=Tt+2TpT\_{\\text{cycle}} = T\_t + 2T\_pTcycle​\=Tt​+2Tp​

where TtT\_tTt​ is the data-frame transmission time and TpT\_pTp​ is the one-way propagation delay.[2]()

Hence link utilization or efficiency is approximately:

η\=TtTt+2Tp\\eta = \\frac{T\_t}{T\_t + 2T\_p}η\=Tt​+2Tp​Tt​​

If we define

a\=TpTt,a = \\frac{T\_p}{T\_t},a\=Tt​Tp​​,

then

η\=11+2a\\eta = \\frac{1}{1 + 2a}η\=1+2a1​

[2]()

This formula explains the bottleneck clearly. When a≪1a \\ll 1a≪1, the frame transmission time dominates and utilization is respectable. When a≫1a \\gg 1a≫1, propagation dominates, so the sender spends most of its time waiting rather than sending.[2]() This is especially harmful on long-distance, satellite, or very high-bandwidth links, where frames are launched quickly but acknowledgments return slowly.[2]()

For example, if a\=10a=10a\=10, then:

η\=121≈0.0476\\eta = \\frac{1}{21} \\approx 0.0476η\=211​≈0.0476

so less than 5%5\\%5% of the time carries useful payload. Some lecture material notes that for satellite links, utilization may drop to around 0.0010.0010.001 or lower under certain parameters, illustrating severe bandwidth waste.

## Footnotes

1. [Data Link Control Protocols - sandilands.info](https://sandilands.info/sgordon/teaching/its323y08s1/protected/ITS323Y08S1L08-DataLinkControlProtocols.pdf) - Lecture notes giving stop-and-wait throughput and efficiency analysis. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-2) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-2-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-2-3) [↩4](https://coursify.hasanraiyan.me/#user-content-fnref-2-4) [↩5](https://coursify.hasanraiyan.me/#user-content-fnref-2-5) [↩6](https://coursify.hasanraiyan.me/#user-content-fnref-2-6) [↩7](https://coursify.hasanraiyan.me/#user-content-fnref-2-7)
 
2. [Simplex Stop and Wait Protocol](https://www.southampton.ac.uk/~sqc/EL336/CNL-5.pdf) - University lecture notes relating stop-and-wait to sliding windows and utilization on LAN and satellite links. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-3) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-3-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-3-3) [↩4](https://coursify.hasanraiyan.me/#user-content-fnref-3-4) [↩5](https://coursify.hasanraiyan.me/#user-content-fnref-3-5) [↩6](https://coursify.hasanraiyan.me/#user-content-fnref-3-6)
 

### 

Stop-and-Wait Efficiency vs. a\=Tp/Tta = T\_p / T\_ta\=Tp​/Tt​

Illustrative values using η\=1/(1+2a)\\eta = 1 / (1 + 2a)η\=1/(1+2a).[2]()

## Footnotes

1. [Data Link Control Protocols - sandilands.info](https://sandilands.info/sgordon/teaching/its323y08s1/protected/ITS323Y08S1L08-DataLinkControlProtocols.pdf) - Lecture notes giving stop-and-wait throughput and efficiency analysis. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-2)
 
2. [Simplex Stop and Wait Protocol](https://www.southampton.ac.uk/~sqc/EL336/CNL-5.pdf) - University lecture notes relating stop-and-wait to sliding windows and utilization on LAN and satellite links. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-3)
 

### Interpreting the Bottleneck

Why does higher bandwidth make Stop-and-Wait worse?

Why are long-distance links a bad match?

Why not just enlarge the frame?

What protocol family solves this better?

### Stop-and-Wait ARQ Recovery from Errors

1. 1
 
 Step 1
 
 Send a numbered frame and start timer
 
 The sender transmits frame 000 or 111 and immediately starts a timeout timer.[2]()
 
 ## Footnotes
 
 1. [The Data Link Layer: ARQ Protocols - MIT](https://web.mit.edu/modiano/www/6.263/lec3-4.pdf) - Detailed explanation of stop-and-wait ARQ, timeouts, and sequence numbers. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
 2. [III. Link Layer ARQ Protocols - CMU](https://mews.sv.cmu.edu/courses/565-w08/files/topic03notes.pdf) - Notes on stop-and-wait ARQ behavior under losses, delays, and retransmissions. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5)
 
 
2. 2
 
 Step 2
 
 Receiver validates the frame
 
 If the frame arrives correctly and matches the expected sequence number, the receiver accepts it, delivers the payload upward, and sends an acknowledgment for the next expected number.[2]()
 
 ## Footnotes
 
 1. [The Data Link Layer: ARQ Protocols - MIT](https://web.mit.edu/modiano/www/6.263/lec3-4.pdf) - Detailed explanation of stop-and-wait ARQ, timeouts, and sequence numbers. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
 2. [III. Link Layer ARQ Protocols - CMU](https://mews.sv.cmu.edu/courses/565-w08/files/topic03notes.pdf) - Notes on stop-and-wait ARQ behavior under losses, delays, and retransmissions. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5)
 
 
3. 3
 
 Step 3
 
 Handle a lost or corrupted frame
 
 If the frame is lost or corrupted, the receiver cannot acknowledge successful receipt. The sender eventually times out because no valid acknowledgment arrives.[2]()
 
 ## Footnotes
 
 1. [The Data Link Layer: ARQ Protocols - MIT](https://web.mit.edu/modiano/www/6.263/lec3-4.pdf) - Detailed explanation of stop-and-wait ARQ, timeouts, and sequence numbers. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
 2. [III. Link Layer ARQ Protocols - CMU](https://mews.sv.cmu.edu/courses/565-w08/files/topic03notes.pdf) - Notes on stop-and-wait ARQ behavior under losses, delays, and retransmissions. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5)
 
 
4. 4
 
 Step 4
 
 Retransmit on timeout
 
 After timeout, the sender retransmits the same numbered frame rather than moving forward.[2]()
 
 ## Footnotes
 
 1. [The Data Link Layer: ARQ Protocols - MIT](https://web.mit.edu/modiano/www/6.263/lec3-4.pdf) - Detailed explanation of stop-and-wait ARQ, timeouts, and sequence numbers. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
 2. [III. Link Layer ARQ Protocols - CMU](https://mews.sv.cmu.edu/courses/565-w08/files/topic03notes.pdf) - Notes on stop-and-wait ARQ behavior under losses, delays, and retransmissions. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5)
 
 
5. 5
 
 Step 5
 
 Handle a lost acknowledgment
 
 If the data frame arrived but the ACK was lost, the sender still times out and retransmits. The receiver recognizes the repeated sequence number as a duplicate and discards the payload while re-sending the ACK.[2]()
 
 ## Footnotes
 
 1. [The Data Link Layer: ARQ Protocols - MIT](https://web.mit.edu/modiano/www/6.263/lec3-4.pdf) - Detailed explanation of stop-and-wait ARQ, timeouts, and sequence numbers. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
 2. [III. Link Layer ARQ Protocols - CMU](https://mews.sv.cmu.edu/courses/565-w08/files/topic03notes.pdf) - Notes on stop-and-wait ARQ behavior under losses, delays, and retransmissions. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5)
 
 
6. 6
 
 Step 6
 
 Handle delayed acknowledgments safely
 
 If an ACK is delayed beyond the timer, retransmission may already have occurred. Sequence numbers let the receiver and sender interpret the event without delivering duplicate data.[2]()
 
 ## Footnotes
 
 1. [The Data Link Layer: ARQ Protocols - MIT](https://web.mit.edu/modiano/www/6.263/lec3-4.pdf) - Detailed explanation of stop-and-wait ARQ, timeouts, and sequence numbers. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
 2. [III. Link Layer ARQ Protocols - CMU](https://mews.sv.cmu.edu/courses/565-w08/files/topic03notes.pdf) - Notes on stop-and-wait ARQ behavior under losses, delays, and retransmissions. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5)
 
 

### Lost Frames, Lost ACKs, and Delayed ACKs

Stop-and-Wait ARQ is designed specifically for noisy or unreliable links where either data frames or acknowledgments may be lost, damaged, or delayed.[2]()

#### 1\. Lost data frame

If the sender transmits a frame and that frame never reaches the receiver, no acknowledgment can be generated. Without a timer, the sender would wait forever. Therefore, timeout is essential: once the timer expires, the sender retransmits the same frame.[2]()

#### 2\. Lost acknowledgment

If the receiver gets the frame correctly and sends the ACK, but the ACK is lost, the sender again sees silence and eventually retransmits.[2]() Now the receiver encounters a duplicate frame. Because the duplicate has the old sequence number, the receiver discards the payload and sends the ACK again rather than delivering the same packet twice.[2]()

#### 3\. Delayed acknowledgment

A delayed ACK is more subtle. The sender may time out and retransmit before the original ACK arrives. When that late ACK eventually appears, the sender must not confuse it with permission for a future frame. Sequence-numbered acknowledgments prevent this ambiguity by tying the ACK to the expected next frame number.[2]()

This recovery method is graceful because no complex rollback is required. The protocol uses only three ideas: detect absence of confirmation, retransmit after timeout, and reject duplicates using sequence numbers.[2]()

## Footnotes

1. [The Data Link Layer: ARQ Protocols - MIT](https://web.mit.edu/modiano/www/6.263/lec3-4.pdf) - Detailed explanation of stop-and-wait ARQ, timeouts, and sequence numbers. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-4-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-4-3) [↩4](https://coursify.hasanraiyan.me/#user-content-fnref-4-4) [↩5](https://coursify.hasanraiyan.me/#user-content-fnref-4-5) [↩6](https://coursify.hasanraiyan.me/#user-content-fnref-4-6) [↩7](https://coursify.hasanraiyan.me/#user-content-fnref-4-7)
 
2. [III. Link Layer ARQ Protocols - CMU](https://mews.sv.cmu.edu/courses/565-w08/files/topic03notes.pdf) - Notes on stop-and-wait ARQ behavior under losses, delays, and retransmissions. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-5-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-5-3) [↩4](https://coursify.hasanraiyan.me/#user-content-fnref-5-4) [↩5](https://coursify.hasanraiyan.me/#user-content-fnref-5-5) [↩6](https://coursify.hasanraiyan.me/#user-content-fnref-5-6)
 
3. [Data Link Layer Protocols](https://web.cs.wpi.edu/~cs513/s07/week3-dllprot.pdf) - Lecture material linking stop-and-wait to sliding-window operation with window size 111. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-7)
 

#### Common Misconception

A timeout does not always mean the data frame was lost. The frame may have arrived successfully, but the acknowledgment may have been lost or delayed.[2]()

## Footnotes

1. [The Data Link Layer: ARQ Protocols - MIT](https://web.mit.edu/modiano/www/6.263/lec3-4.pdf) - Detailed explanation of stop-and-wait ARQ, timeouts, and sequence numbers. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
2. [III. Link Layer ARQ Protocols - CMU](https://mews.sv.cmu.edu/courses/565-w08/files/topic03notes.pdf) - Notes on stop-and-wait ARQ behavior under losses, delays, and retransmissions. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5)
 

more...

Basic Stop-and-Wait

Stop-and-Wait ARQSliding Window View

Used primarily for flow control on an ideal or noiseless link. Sender sends one frame and waits. ACK mainly acts as permission to continue.[2]()

## Footnotes

1. [Data-link Control & Protocols](https://www.tutorialspoint.com/data_communication_computer_network/data_link_control_and_protocols.htm) - Overview of data link layer flow control and stop-and-wait basics. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1)
 
2. [Simplex Stop and Wait Protocol](https://www.southampton.ac.uk/~sqc/EL336/CNL-5.pdf) - University lecture notes relating stop-and-wait to sliding windows and utilization on LAN and satellite links. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-3)
 

### 

Lifecycle of a Stop-and-Wait ARQ Exchange

#### Frame Transmission

Stage 1

The sender emits one numbered frame and starts a timer.[2]()"

## Footnotes

1. [The Data Link Layer: ARQ Protocols - MIT](https://web.mit.edu/modiano/www/6.263/lec3-4.pdf) - Detailed explanation of stop-and-wait ARQ, timeouts, and sequence numbers. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
2. [III. Link Layer ARQ Protocols - CMU](https://mews.sv.cmu.edu/courses/565-w08/files/topic03notes.pdf) - Notes on stop-and-wait ARQ behavior under losses, delays, and retransmissions. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5)
 

#### Link Uncertainty

Stage 2

The frame or its acknowledgment may be delayed, corrupted, or lost.[2]()"

## Footnotes

1. [The Data Link Layer: ARQ Protocols - MIT](https://web.mit.edu/modiano/www/6.263/lec3-4.pdf) - Detailed explanation of stop-and-wait ARQ, timeouts, and sequence numbers. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
2. [III. Link Layer ARQ Protocols - CMU](https://mews.sv.cmu.edu/courses/565-w08/files/topic03notes.pdf) - Notes on stop-and-wait ARQ behavior under losses, delays, and retransmissions. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5)
 

#### ACK Reception or Timeout

Stage 3

If the correct ACK arrives in time, the sender advances; otherwise, timeout occurs.[2]()"

## Footnotes

1. [The Data Link Layer: ARQ Protocols - MIT](https://web.mit.edu/modiano/www/6.263/lec3-4.pdf) - Detailed explanation of stop-and-wait ARQ, timeouts, and sequence numbers. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
2. [III. Link Layer ARQ Protocols - CMU](https://mews.sv.cmu.edu/courses/565-w08/files/topic03notes.pdf) - Notes on stop-and-wait ARQ behavior under losses, delays, and retransmissions. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5)
 

#### Retransmission

Stage 4

The sender resends the same sequence-numbered frame.[2]()"

## Footnotes

1. [The Data Link Layer: ARQ Protocols - MIT](https://web.mit.edu/modiano/www/6.263/lec3-4.pdf) - Detailed explanation of stop-and-wait ARQ, timeouts, and sequence numbers. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
2. [III. Link Layer ARQ Protocols - CMU](https://mews.sv.cmu.edu/courses/565-w08/files/topic03notes.pdf) - Notes on stop-and-wait ARQ behavior under losses, delays, and retransmissions. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5)
 

#### Duplicate Suppression

Stage 5

The receiver discards repeated frames and reissues the appropriate ACK.[2]()"

## Footnotes

1. [The Data Link Layer: ARQ Protocols - MIT](https://web.mit.edu/modiano/www/6.263/lec3-4.pdf) - Detailed explanation of stop-and-wait ARQ, timeouts, and sequence numbers. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
2. [III. Link Layer ARQ Protocols - CMU](https://mews.sv.cmu.edu/courses/565-w08/files/topic03notes.pdf) - Notes on stop-and-wait ARQ behavior under losses, delays, and retransmissions. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5)
 

#### Progress to Next Frame

Stage 6

Once the sender gets the expected ACK, it toggles sequence number and continues.[2]()"

## Footnotes

1. [The Data Link Layer: ARQ Protocols - MIT](https://web.mit.edu/modiano/www/6.263/lec3-4.pdf) - Detailed explanation of stop-and-wait ARQ, timeouts, and sequence numbers. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
2. [Data Link Layer Protocols](https://web.cs.wpi.edu/~cs513/s07/week3-dllprot.pdf) - Lecture material linking stop-and-wait to sliding-window operation with window size 111. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-7)
 

### Strengths, Limitations, and Place in the Data Link Layer

Stop-and-Wait remains pedagogically and practically important because it isolates the core ideas behind reliable data transfer: pacing, acknowledgment, timeout, retransmission, and duplicate detection.[2]() Its implementation cost is low, buffer needs are minimal, and correctness is comparatively easy to verify.[2]()

However, its limits are fundamental:

- only one outstanding frame is allowed, so the link is often idle[2]()
- throughput collapses as round-trip propagation delay grows[2]()
- performance becomes poor on high bandwidth-delay product links[2]()
- even when errors are rare, waiting for every ACK wastes capacity[2]()

Thus, Stop-and-Wait is best understood as the conceptual foundation for more capable ARQ schemes such as Go-Back-N and Selective Repeat, which keep multiple frames in flight to improve utilization.[2]()

A compact way to summarize the protocol is:

Correctness≈ACKs+timeout+sequence numbers\\text{Correctness} \\approx \\text{ACKs} + \\text{timeout} + \\text{sequence numbers}Correctness≈ACKs+timeout+sequence numbers

while its main performance issue is:

Low utilization when 2Tp≫Tt\\text{Low utilization when } 2T\_p \\gg T\_tLow utilization when 2Tp​≫Tt​

[2]()

## Footnotes

1. [Data-link Control & Protocols](https://www.tutorialspoint.com/data_communication_computer_network/data_link_control_and_protocols.htm) - Overview of data link layer flow control and stop-and-wait basics. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1)
 
2. [The Data Link Layer: ARQ Protocols - MIT](https://web.mit.edu/modiano/www/6.263/lec3-4.pdf) - Detailed explanation of stop-and-wait ARQ, timeouts, and sequence numbers. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-4-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-4-3)
 
3. [Data Link Layer Protocols](https://web.cs.wpi.edu/~cs513/s07/week3-dllprot.pdf) - Lecture material linking stop-and-wait to sliding-window operation with window size 111. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-7)
 
4. [Data Link Control Protocols - sandilands.info](https://sandilands.info/sgordon/teaching/its323y08s1/protected/ITS323Y08S1L08-DataLinkControlProtocols.pdf) - Lecture notes giving stop-and-wait throughput and efficiency analysis. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-2) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-2-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-2-3) [↩4](https://coursify.hasanraiyan.me/#user-content-fnref-2-4) [↩5](https://coursify.hasanraiyan.me/#user-content-fnref-2-5)
 
5. [Simplex Stop and Wait Protocol](https://www.southampton.ac.uk/~sqc/EL336/CNL-5.pdf) - University lecture notes relating stop-and-wait to sliding windows and utilization on LAN and satellite links. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-3) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-3-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-3-3) [↩4](https://coursify.hasanraiyan.me/#user-content-fnref-3-4) [↩5](https://coursify.hasanraiyan.me/#user-content-fnref-3-5)
 
6. [III. Link Layer ARQ Protocols - CMU](https://mews.sv.cmu.edu/courses/565-w08/files/topic03notes.pdf) - Notes on stop-and-wait ARQ behavior under losses, delays, and retransmissions. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5)
 

### Knowledge Check

Question 1 of 5

Q1Single choice

What is the primary purpose of flow control in the Stop-and-Wait protocol?

To match sender transmission rate with receiver processing capacity

To encrypt frames before transmission

To eliminate the need for acknowledgments

To increase the physical signal speed

BackNext

[Previous\\ \\ Cyclic Redundancy Check (CRC)](https://coursify.hasanraiyan.me/course/network-theory/cyclic-redundancy-check-crc) [Next\\ \\ Sliding Window Protocols (Go-Back-N & Selective Repeat ARQ)](https://coursify.hasanraiyan.me/course/network-theory/sliding-window-protocols-go-back-n-selective-repeat-arq)