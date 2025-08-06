# Ports
A port is simply a number in networking that's used to identify a specific service or process running on a machine

**Example**
| IP Address    | Port | Service        |
| ------------- | ---- | -------------- |
| 192.168.1.100 | 22   | SSH            |
| 192.168.1.100 | 80   | Web server     |
| 192.168.1.100 | 3306 | MySQL database |

Even though all services run on the same IP, the port number helps route the traffic to the correct application.

# Protocols
A protocol is a set of rules that defines how data is transmitted between devices in a network.
## 🔀 **TCP vs UDP**
| Feature               | **TCP** (Transmission Control Protocol) | **UDP** (User Datagram Protocol)   |
| --------------------- | --------------------------------------- | ---------------------------------- |
| 🔗 **Connection**     | Connection-oriented                     | Connectionless                     |
| ✅ **Reliability**     | Reliable (guarantees delivery)          | Not reliable (no guarantee)        |
| 🔁 **Data Order**     | Data arrives in the correct order       | Data may arrive out of order       |
| 📥 **Acknowledgment** | Sends ACKs to confirm receipt           | No acknowledgment                  |
| 🐢 **Speed**          | Slower (due to handshakes, error check) | Faster (no overhead)               |
| 🧱 **Use Cases**      | Web (HTTP/HTTPS), SSH, FTP, Email       | DNS, Video Streaming, VoIP, Gaming |
| 🔐 **Handshake**      | Yes (3-way handshake)                   | No handshake                       |
| 🔄 **Resend Packets** | Yes, if lost                            | No automatic resend                |

## 📦 Common Types of Protocols:
| Protocol  | Type    | Purpose                  | Port Example |
| --------- | ------- | ------------------------ | ------------ |
| **HTTP**  | TCP     | Web traffic (insecure)   | 80           |
| **HTTPS** | TCP     | Web traffic (secure/SSL) | 443          |
| **FTP**   | TCP     | File Transfer            | 21           |
| **SSH**   | TCP     | Secure remote login      | 22           |
| **DNS**   | UDP/TCP | Domain name resolution   | 53           |
| **SMTP**  | TCP     | Sending emails           | 25           |
| **SNMP**  | UDP     | Network monitoring       | 161          |
| **NTP**   | UDP     | Time synchronization     | 123          |
---
### 🔹 **TCP (Transmission Control Protocol)**
* Connection-oriented
* Reliable, ordered delivery
* Used for web, SSH, FTP, email, etc.
### 🔸 **UDP (User Datagram Protocol)**
* Connectionless
* Faster, but no guarantee of delivery
* Used for DNS, video streaming, VoIP, etc.

* **TCP** is like a phone call — both sides connect, speak clearly, and confirm delivery.
* **UDP** is like sending a letter — it might arrive, or it might get lost, but it’s fast and doesn't wait for confirmation.

# Firewalls

# Ingress/Inbound
# Egress/Outbound

# Stateless firewalls
- The response traffic not allowed automatically.Explicitly allow the return traffic[Ex:NACLS]
- Most of the firewalls are stateless by nature
# Stateful firewalls
- The response traffic automatically allowed then we call as stateful firewalls[EX:SG,NetowrkPolicies]
- They store state of incoming request so that when ever they replay they know they are replaying same connection that was initiated before 
- If originating traffic is allow automatically response traffic is allowed
# Ephemeral ports

# Network Access Controls List[NACL] 

# Security Groups
1. Firewalls at instance level
2. 