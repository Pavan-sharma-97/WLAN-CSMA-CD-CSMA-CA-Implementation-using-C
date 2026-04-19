# WLAN-CSMA-CD-CSMA-CA-Implementation-using-C

## 📡 Project Overview

This project presents a **high-fidelity simulation of medium access control (MAC) protocols** used in wired and wireless networks—**CSMA/CD (Carrier Sense Multiple Access with Collision Detection)** and **CSMA/CA (Carrier Sense Multiple Access with Collision Avoidance)**—implemented in **C using POSIX threads**.

The simulation models multiple network nodes sharing a common communication medium, contending for access, sensing the channel, handling collisions, and applying protocol‑specific strategies to ensure reliable data transmission. The goal is to offer a **conceptual and practical understanding of WLAN/Ethernet MAC-layer behavior** rather than to replicate hardware-level timing with absolute precision.

This project is ideal for:

*   Computer Networks coursework
*   WLAN protocol analysis
*   MAC-layer behavior visualization
*   Operating Systems and concurrency demonstrations

***

## 🎯 Objectives

*   Simulate **multi-node communication** over a shared medium
*   Implement and compare **CSMA/CD (Ethernet)** and **CSMA/CA (IEEE 802.11 WLAN)**
*   Demonstrate **collision detection vs. collision avoidance**
*   Use **thread-based concurrency** to represent independent network stations
*   Provide timestamp‑based visualization of transmission behavior

***

## 🧠 Protocol Concepts Implemented

### 🔹 CSMA/CD (Carrier Sense Multiple Access with Collision Detection)

Used in **wired Ethernet networks**, where nodes:

1.  Sense the channel before transmitting
2.  Begin transmission if the channel is idle
3.  Monitor the channel during transmission
4.  Detect collisions and abort transmission
5.  Retry after a random backoff period

✔ Implemented through:

*   Shared global channel state
*   Concurrent access via threads
*   Timestamp/sequence number comparison
*   Collision detection during transmission

***

### 🔹 CSMA/CA (Carrier Sense Multiple Access with Collision Avoidance)

Used in **wireless LANs (WLANs)**, where collision detection is not feasible due to signal attenuation.

Key mechanisms:

1.  Channel sensing before transmission
2.  Random backoff before access
3.  Collision minimization instead of detection
4.  Retry upon transmission failure

✔ Simulated through:

*   Deferred transmission logic
*   Backoff delays
*   Timestamp-based conflict checks
*   Avoidance-based retry strategy

***

## ⚙️ System Architecture

### 🧵 Thread-Based Node Simulation

*   Each network station is implemented as an independent **POSIX thread**
*   Threads operate concurrently to simulate real-world contention
*   Each node:
    *   senses the channel
    *   attempts transmission
    *   detects or avoids collisions
    *   logs transmission outcomes

### 🌐 Shared Medium Model

*   A global shared variable acts as the **logical communication channel**
*   Channel state changes represent transmission activity
*   Lack of synchronization intentionally demonstrates contention effects

### ⏱ Timestamp Mechanism

*   `gettimeofday()` is used to log transmission times
*   Sequence values compare channel state before and after transmission
*   Used for detecting interference during transmission windows

***

## 🛠 Technologies Used

*   **Language**: C (GNU C)
*   **Concurrency**: POSIX Threads (pthread)
*   **Timing**: `gettimeofday()`, `usleep()`
*   **Signal Handling**: `SIGINT` for graceful exit
*   **Platform**: Linux / UNIX-based systems

***

## 📄 Key Features

*   ✅ Multi-node concurrent transmission
*   ✅ MAC-layer protocol simulation
*   ✅ Collision detection (CSMA/CD)
*   ✅ Collision avoidance strategy (CSMA/CA)
*   ✅ Real-time timestamp logging
*   ✅ Infinite simulation with graceful interrupt handling
*   ✅ Lightweight and dependency-free implementation

***

## 📊 Sample Output Behavior

*   Node starts transmission with timestamp
*   Another node interrupts → collision detected/avoided
*   Frame retransmission after delay
*   Successful transmission confirmation

This textual output helps visualize **network contention in real time**.

***

## ⚠️ Design Limitations (Intentional for Learning)

*   No mutex protection on shared variables (to expose race conditions)
*   Logical simulation only (not hardware-accurate timing)
*   Simplified backoff strategies
*   Not IEEE‑standard‑compliant timing values

These limitations are **intentional** to keep the implementation transparent and educational.

***

## 📚 Educational Value

This project helps learners understand:

*   Differences between **wired vs. wireless MAC protocols**
*   Why CSMA/CD is unsuitable for WLANs
*   How contention impacts throughput
*   Thread synchronization challenges
*   MAC protocol design trade-offs

***

## 🚀 Future Improvements

*   Add mutexes and condition variables
*   Implement exponential backoff algorithms
*   Separate CSMA/CD and CSMA/CA modules
*   Collect performance metrics (throughput, delays)
*   Visualize traffic using logs or graphs

***

## ✅ Conclusion

This project provides a **clear, concise, and effective simulation of CSMA/CD and CSMA/CA protocols**, emphasizing protocol behavior, concurrency, and collision handling. It is well-suited for academic demonstrations, lab submissions, and networking portfolios, offering strong conceptual clarity and extensibility.

***

