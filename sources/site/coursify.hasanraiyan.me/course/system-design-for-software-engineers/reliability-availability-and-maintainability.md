# Source: https://coursify.hasanraiyan.me/course/system-design-for-software-engineers/reliability-availability-and-maintainability

# Reliability, Availability, and Maintainability

These three concepts are the cornerstones of building software systems that people can trust and engineers can manage.

### 1\. Reliability

A reliable system is one that continues to work correctly (performing the right function at the desired level of performance) even when things go wrong. Things that go wrong are called **faults**, and systems that anticipate and cope with faults are called **fault-tolerant**.

- **Hardware Faults**: Hard disks crashing, RAM becoming faulty, power outages.
- **Software Faults**: Bugs, runaway processes that consume resources, slow dependencies.
- **Human Errors**: Misconfigurations, accidental deletion of data.

#### How to build reliable systems?

- **Redundancy**: Having multiple copies of components.
- **Isolation**: Ensuring a failure in one component doesn't take down others.
- **Monitoring & Alerting**: Knowing when something is wrong immediately.

### 2\. Availability

Availability is the percentage of time a system is operational and reachable by users.

- **High Availability (HA)**: Systems designed to be available almost all the time.
- **Measuring Availability**: Expressed in "nines".
 - 99% ("two nines"): 3.65 days of downtime per year.
 - 99.9% ("three nines"): 8.77 hours of downtime per year.
 - 99.99% ("four nines"): 52.6 minutes of downtime per year.
 - 99.999% ("five nines"): 5.26 minutes of downtime per year.

**Reliability vs Availability**: A system can be reliable but not available (e.g., it works perfectly but is unreachable due to a network cut), or available but not reliable (e.g., you can reach it, but it returns errors).

### 3\. Maintainability

Maintainability is the ease with which a system can be understood, modified, and operated.

- **Operability**: Making it easy for operations teams to keep the system running smoothly.
- **Simplicity**: Managing complexity so that new engineers can understand the system.
- **Evolvability**: Making it easy for engineers to make changes to the system in the future.

### Knowledge Check

Question 1 of 3

Q1Single choice

What is the difference between a fault and a failure?

They are the same thing.

A fault is a component deviating from spec; a failure is the system as a whole failing to provide service.

A failure is a component deviating from spec; a fault is the system as a whole failing to provide service.

Faults are hardware-related whereas failures are software-related.

BackNext

[Previous\\ \\ Scalability: Vertical vs Horizontal](https://coursify.hasanraiyan.me/course/system-design-for-software-engineers/scalability-vertical-vs-horizontal) [Next\\ \\ Performance Metrics: Latency vs Throughput](https://coursify.hasanraiyan.me/course/system-design-for-software-engineers/performance-metrics-latency-vs-throughput)