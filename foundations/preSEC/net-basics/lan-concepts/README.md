# LAN Concepts

> This section will explore the key ideas behind Local Area Networks (LANs), including the different ways to lay them out, known as topologies.

---

## 1. LAN Topologies

When we talk about a LAN, the word "topology" might sound complicated, but it really just means the design or layout of the network. Think of it as the blueprint for how all the devices are connected to each other.

We'll cover three main topologies here.

### 1.1. Star Topology

The main idea of a star topology is that every device—whether it's a PC, a printer, or anything else—is individually connected to a central network device, like a switch or a hub. This is the most common topology found today because it's so reliable and easy to expand.

<p align="center">
  <img src="assets/images/star-topology-diagram.png" alt="Star Topology Diagram" width="600"/>
  <br/>
  <em>Figure 1: A diagram of a Star Topology network.</em>
</p>

*   **Advantages:**
    *   **Reliable:** If one cable fails, only one device loses its connection. The rest of the network keeps working just fine.
    *   **Scalable:** Want to add a new computer? Just run a new cable to the central hub. It's that simple!

*   **Disadvantages:**
    *   **Expensive:** Because every device needs its own cable and you have to buy a dedicated central device (like a switch), the cost is higher than other topologies.
    *   **Single Point of Failure:** Although it's rare because central devices are often built to be robust, if that central hub fails—the entire network goes down.
    *   **Maintenance & Troubleshooting:** The bigger the network gets, the more complex it is to maintain. Finding faults can also become much harder.

---

### 1.2. Bus Topology

A bus topology relies on a single main cable known as a "backbone." You can picture it like the main branch of a tree, where all the network devices are like leaves stemming from it.

<p align="center">
  <img src="assets/images/bus-topology-diagram.png" alt="Bus Topology Diagram" width="600"/>
  <br/>
  <em>Figure 2: A diagram of a Bus Topology network.</em>
</p>

*   **Advantages:**
    *   **Cheap & Easy to Set Up:** This is one of the cheapest and easiest topologies to install because you just need one main cable and don't need a lot of expensive networking gear.

*   **Disadvantages:**
    *   **Easily Bottlenecked:** All data travels on the same cable. If many devices try to send data at once, the network gets slow and congested—like a traffic jam.
    *   **Hard to Troubleshoot:** With all the data running along the same path, it's very difficult to pinpoint which device is causing problems when an issue occurs.
    *   **No Redundancy:** If that main "backbone" cable breaks anywhere, the entire network fails.

---

### 1.3. Ring Topology

In a ring topology, devices are connected directly to each other in a closed loop. This setup requires less cabling and doesn't depend on an expensive central device like a star topology does.

<p align="center">
  <img src="assets/images/ring-topology-diagram.png" alt="Ring Topology Diagram" width="600"/>
  <br/>
  <em>Figure 3: A diagram of a Ring Topology network.</em>
</p>

*   **How it Works:** Data is sent around the ring, passing from one device to the next until it reaches its destination. An interesting rule here is that a device will only forward data from another device if it doesn't have any of its own data to send. If it does, it will send its own data first.

*   **Advantages:**
    *   **Fewer Bottlenecks:** It's less prone to bottlenecks than a bus topology because large amounts of traffic aren't all competing on the same line at the same time.
    *   **Easy to Troubleshoot:** It's fairly straightforward to find faults on the network.

*   **Disadvantages:**
    *   **Inefficient Data Travel:** Data might have to hop through many other devices before it gets where it needs to go, which isn't very efficient.
    *   **Entire Network Can Fail:** This is a double-edged sword. A single fault—like a cut cable or a broken device—breaks the loop and brings the entire network down.