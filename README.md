# SISTEM OPERASI  
## INTRODUCTION TO OS

**Oleh:**  
Siti Romzatul Alimah  
D3 Teknik Informatika (A) PENS LA  
NRP 3124521019  
Dosen Pembimbing: Dr Ferry Astika Saputra ST, M.Sc  

**POLITEKNIK ELEKTRONIKA NEGERI SURABAYA**  
**TAHUN PELAJARAN 2024/2025**

---

## PRACTICE EXERCISE

### Q1: What are the three main purposes of an operating system?
- **Resource Management:** Allocating and managing system resources like CPU, memory, and I/O devices.
- **User Interface:** Providing an environment where users can interact with the computer system.
- **Program Execution:** Enabling the execution and management of applications.

### Q2: We have stressed the need for an operating system to make efficient use of the computing hardware.  
**When is it appropriate for the operating system to forsake this principle and to "waste" resources? Why is such a system not really wasteful?**
- **Answer:**  
  - When prioritizing user convenience, security, or compatibility over efficiency.
  - For example, virtual memory may "waste" disk space but allows applications to run smoothly.
  - Not truly wasteful since it enhances usability and system stability.

### Q3: What is the main difficulty that a programmer must overcome in writing an operating system for a real-time environment?
- **Answer:**  
  - Guaranteeing time constraints (tasks must complete within a strict deadline).
  - Managing priorities to ensure critical tasks execute first.
  - Ensuring reliability and security in time-sensitive environments.

### Q4: Keeping in mind the various definitions of operating system, should the OS include applications such as web browsers and mail programs?  
**Argue both that it should and that it should not, and support your answers.**
- **Yes:** Improves user experience, provides essential tools, and ensures system compatibility.
- **No:** Bloats the OS, increases security risks, and reduces flexibility.

### Q5: How does the distinction between kernel mode and user mode function as a rudimentary form of protection (security)?
- **Answer:**  
  - User mode restricts access to critical system resources.
  - Kernel mode allows privileged operations but prevents unauthorized access.

### Q6: Which of the following instructions should be privileged?
- **a. Set value of timer**  
- **b. Read the clock**  
- **c. Clear memory**  
- **d. Issue a trap instruction**  
- **e. Turn off interrupts**  
- **f. Modify entries in device-status table**  
- **g. Switch from user to kernel mode**  
- **h. Access I/O device**

**Privileged:** a, c, e, f, g  
**Not Privileged:** b, d, h

### Q7: Some early computers protected the operating system by placing it in a memory partition that could not be modified by either the user job or the operating system itself.  
**Describe two difficulties that could arise with such a scheme.**
- **Answer:**  
  - Lack of flexibility – Hard to update or expand.
  - Memory fragmentation – Can lead to inefficient memory usage.

### Q8: Some CPUs provide for more than two modes of operation.  
**What are two possible uses of these multiple modes?**
- **Answer:**  
  - Intermediate privilege levels for different types of system processes (e.g., device drivers).
  - Enhanced security by preventing applications from accessing critical OS functions directly.

### Q9: Timers could be used to compute the current time.  
**Provide a short description of how this could be accomplished.**
- **Answer:**  
  - By generating periodic interrupts and counting the number of interrupts since boot.

### Q10: Give two reasons why caches are useful.  
**What problems do they solve? What problems do they cause? If a cache can be made as large as the device for which it is caching (for instance, a cache as large as a disk), why not make it that large and eliminate the device?**
- **Benefits:**  
  - Speeds up data access by storing frequently used data.
  - Reduces latency and decreases load on main memory.
- **Problems:**  
  - Cache coherence issues.
  - Limited capacity.
- **Why not replace disks with caches?**  
  - Caches are expensive, volatile, and lack long-term storage capabilities.

### Q11: Distinguish between the client-server and peer-to-peer models of distributed systems.
- **Client-Server:**  
  - Centralized control; the server provides services to multiple clients.
  - Easier to manage and secure.
- **Peer-to-Peer:**  
  - Decentralized architecture; each node acts as both client and server.
  - More fault-tolerant.

---

## CHAPTER 1 EXERCISES

### Q1.12: How do clustered systems differ from multiprocessor systems?  
**What is required for two machines in a cluster to provide a highly available service?**
- **Multiprocessor:** Multiple CPUs share memory.
- **Clustered:** Multiple machines work together over a network.
- **High Availability Requirements:** Shared storage and failover mechanisms.

### Q1.13: Consider a computing cluster with two nodes running a database.  
**Describe two ways to manage disk access and discuss their benefits and disadvantages.**
- **Shared Disk:**  
  - Both nodes access the same disk.
  - **Benefits:** Simpler implementation.
  - **Disadvantages:** Requires careful synchronization to avoid data corruption.
- **Distributed File System:**  
  - Data is distributed across multiple disks with managed access.
  - **Benefits:** Improved fault tolerance and scalability.
  - **Disadvantages:** More complex implementation.

### Q1.14: What is the purpose of interrupts? How does an interrupt differ from a trap? Can traps be generated intentionally by a user program?  
- **Purpose of Interrupts:**  
  - They allow the CPU to respond to asynchronous hardware events without constant polling.
- **Interrupt vs. Trap:**  
  - Interrupts originate from hardware; traps are software-generated (e.g., for system calls or errors).
- **Intentional Traps:**  
  - Yes, user programs can trigger traps to request OS services or handle exceptions.

### Q1.15: Explain how the Linux kernel variables `HZ` and `jiffies` can be used to determine system uptime.
- **HZ:** Number of clock ticks per second.
- **jiffies:** A global counter that increments with each tick.
- **Calculation:** Uptime (seconds) ≈ `jiffies` / `HZ`.

### Q1.16: Direct Memory Access (DMA) for high-speed I/O.
#### a. How does the CPU interface with the device to coordinate the transfer?
- **Answer:**  
  The CPU configures the DMA controller (specifying source/destination addresses and transfer size) and then the DMA controller handles the transfer autonomously.

#### b. How does the CPU know when the memory operations are complete?
- **Answer:**  
  The DMA controller issues an interrupt to the CPU upon completion.

#### c. Does DMA interfere with the execution of user programs?
- **Answer:**  
  Yes, due to bus contention (which may slow memory access) and potential cache coherence issues if the DMA updates memory while the CPU's cache is outdated.

### Q1.17: Is it possible to construct a secure operating system on systems without hardware privileged mode?  
- **Yes:**  
  Software isolation techniques (e.g., sandboxing, virtual machines, type-safe languages) can be used.
- **No:**  
  Lack of hardware-enforced protections makes it harder to prevent unauthorized access to critical resources.

### Q1.18: Why do many SMP systems have different levels of caches?
- **Answer:**  
  Local caches (e.g., L1) provide fast, low-latency access for each core, while shared caches (e.g., L2/L3) ensure data consistency and reduce duplication, balancing speed, size, and cost.

### Q1.19: Rank the following storage systems from slowest to fastest:
- **Magnetic tapes**  
- **Optical disk**  
- **Hard-disk drives**  
- **Nonvolatile memory**  
- **Main memory**  
- **Cache**  
- **Registers**

### Q1.20: Consider an SMP system similar to Figure 1.8.  
**Illustrate with an example how data in memory could have different values in each of the local caches.**
- **Answer:**  
  Two processors (A and B) each have their own L1 cache. Both load variable X from main memory. If processor A updates X in its cache without writing back immediately, A’s cache holds a new value while B’s cache retains the old value.

### Q1.21: Discuss how maintaining cache coherence is a challenge in:
#### a. Single-processor systems
- **Answer:**  
  Hardware ensures coherence between cache levels (e.g., L1 and L2).

#### b. Multiprocessor systems
- **Answer:**  
  Each core’s cache may become outdated if one core updates a shared variable; protocols like MESI synchronize caches.

#### c. Distributed systems
- **Answer:**  
  Independent caches on different nodes can become stale; explicit mechanisms (e.g., versioning or invalidation protocols) are needed.

### Q1.22: Describe a mechanism for enforcing memory protection.
- **Answer:**  
  Paging with an MMU provides each process its own virtual address space with page tables defining access rights. Unauthorized access triggers a fault, preventing one process from modifying another’s memory.

### Q1.23: Which network configuration best suits the following environments?
- **a. Campus Student Union:** LAN  
- **b. Several Campus Locations:** WAN  
- **c. Neighborhood:** LAN

### Q1.24: Describe some challenges of designing OS for mobile devices versus traditional PCs.
- **Answer:**  
  Mobile devices face limited battery life, lower processing power, smaller memory, need for touch-optimized interfaces, variable network conditions, and diverse hardware sensors.

### Q1.25: What are some advantages of peer-to-peer systems over client-server systems?
- **Answer:**  
  Peer-to-peer systems are decentralized, scalable, and reduce the need for expensive server infrastructure.

### Q1.26: Describe distributed applications appropriate for a peer-to-peer system.
- **Answer:**  
  Examples include file sharing (e.g., BitTorrent), decentralized communication (VoIP, messaging), blockchain-based cryptocurrencies, and distributed storage networks.

### Q1.27: Identify several advantages and disadvantages of open-source operating systems.  
**Advantages:**
- **Free & Flexible:** Appeals to developers, hobbyists, and cost-sensitive users.
- **Transparent & Secure:** Valued by security experts and researchers.

**Disadvantages:**
- **Limited Official Support:** Can be problematic for enterprises needing reliable support.
- **Fragmentation & Complexity:** May challenge non-technical users.

---
