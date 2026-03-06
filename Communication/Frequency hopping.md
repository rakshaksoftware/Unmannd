# Frequency Hopping Communication in Drones

## Overview

Reliable communication between drones is critical for coordination and control. One robust method used in wireless systems is **Frequency Hopping Spread Spectrum (FHSS)**. This technique improves resistance to interference and jamming by continuously changing the transmission frequency according to a shared algorithm.

---

# Communication Setup

Communication between a transmitter and receiver occurs as follows:

1. The **transmitter sends a signal at a specific frequency**.
2. The **receiver applies a band-pass filter** tuned to that frequency.
3. Only signals within the filter band are received and processed.

This allows the receiver to isolate the intended signal from other frequencies.

---

# Continuous Frequency Change

To prevent interception or jamming, the communication frequency between the two drones **changes continuously over time**.

This is achieved using:

**FHSS — Frequency Hopping Spread Spectrum**

In FHSS:

* Both transmitter and receiver run the **same algorithm**.
* The algorithm generates the **next communication frequency**.
* Because both devices run the same algorithm with the same inputs, they always hop to the **same frequency at the same time**.
* External observers cannot easily predict the next frequency.

---

# Key Parameters of Frequency Hopping

Two important parameters define the hopping sequence:

### 1. Starting Value (Seed)

The initial value used by the frequency generation algorithm.

### 2. Hop Interval

The time after which the communication frequency changes.

Both transmitter and receiver must agree on these parameters.

---

# Synchronization Mechanism

To ensure both devices stay synchronized:

1. The **transmitter sends a synchronization packet**.
2. This packet is sent on a **predetermined channel called the Control Channel**.
3. The synchronization packet contains:

   * The **seed value**
   * Timing information

Once the receiver obtains this packet:

* It **initializes the algorithm**
* Both systems begin **frequency hopping simultaneously**.

---

# Determining the Starting Point

Each transmitted packet may contain synchronization information.

When the receiver receives the packet:

1. It **resets its internal timer to zero**.
2. The propagation delay is usually **ignored** because it is extremely small.
3. The early portion of each hop is often treated as a **dead window**, during which hardware switches to the next channel.

---



# Linear Feedback Shift Register (LFSR)

An **LFSR** is commonly used for generating pseudo-random sequences.

### Characteristics

* Generates sequences that appear random.
* Requires **very low computational power**.
* Efficient for **embedded communication systems**.

Because of these properties, LFSRs are widely used in FHSS systems.

---

# Handling Control Channel Jamming

A jammer may attempt to block communication by interfering with the control channel.

Two possible cases arise:

---

# Case A — Jammer Detects Transmitted Frequencies

In this scenario:

### Transmitter

* Continues hopping across **125 channels** rapidly.
* Example hopping interval: **10 ms**.

### Receiver

* Stops searching for the control channel.
* Waits on a **single channel (e.g., Channel 1)** for a long time (~500 ms).

### Intersection

Since the transmitter cycles through all channels quickly, it will eventually land on the receiver's listening channel.

### Lock Acquisition

When the receiver detects a packet:

1. It reads the **seed and timestamp**.
2. It immediately synchronizes with the transmitter's hopping sequence.

---

# Case B — Jammer Targets Only the Control Channel

If the jammer only blocks the control channel:

* The **transmitter continues hopping** across frequencies.
* The **receiver attempts communication on other frequencies**.
* Once they intersect on the same frequency, communication resumes.

# Advancements in Frequency Hopping

Recent research has introduced improvements such as:

### Quantum Random Number Generators

Used to produce **truly random seeds**, improving unpredictability and security.

### Adaptive Frequency Hopping (AFH)

The system dynamically **avoids frequencies experiencing interference or jamming**.

---


