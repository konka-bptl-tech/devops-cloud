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

Great question Konka! Let's clear your confusion with a simple explanation 👇

---

## ✅ First: **Are HTTP and HTTPS protocols?**

> **Yes.**
> **HTTP (HyperText Transfer Protocol)** and **HTTPS (HTTP Secure)** are **application layer protocols** used for web communication.

* They define **how web browsers and servers exchange data** (like loading websites).
* **HTTPS** is just **HTTP + SSL/TLS encryption** for secure communication.

---

## ✅ Then what is **TCP**?

> **TCP (Transmission Control Protocol)** is a **transport layer protocol**.

It defines **how data should be sent across a network**, making sure it:

* Arrives in order
* Has no errors
* Is acknowledged

---

## 🤝 How do they work together?

Think of it like layers:

```
Application Layer  →  HTTP / HTTPS
Transport Layer    →  TCP
Network Layer      →  IP
```

When you open a website:

1. **HTTP/HTTPS** defines **what data is being sent** (like a GET request for a web page).
2. **TCP** ensures that data is **reliably delivered** between your browser and the server.


## 🎯 Simple Analogy:

* **HTTP/HTTPS** = What you're saying (the message content)
* **TCP** = How you send the message (in an envelope with tracking)

### 🧪 Real Example:

When you visit:

```
https://example.com
```

* Your browser uses **HTTPS** to communicate with the server.
* HTTPS uses **TCP** to reliably send and receive that data.

--- 
# Firewalls
> A **firewall** is a **security system** that controls the **incoming and outgoing network traffic** based on **rules**.

It acts like a **gatekeeper** that decides whether to **allow or block traffic** between your device (or network) and the internet or other networks.

---

### 🔐 You can say:

> **"A firewall filters network traffic based on IP address, port number, and protocol, and only allows traffic that matches defined security rules."**

---

## 🧱 Types of Firewalls

| Type                | Description                                                                  |
| ------------------- | ---------------------------------------------------------------------------- |
| **Host-based**      | Installed on individual machines (e.g., Windows Firewall, iptables on Linux) |
| **Network-based**   | Deployed at network level (e.g., between LAN and Internet)                   |
| **Cloud Firewalls** | AWS Security Groups, Azure NSGs, GCP firewall rules                          |

---

## 📦 What Can It Filter?

* **IP Address** (source or destination)
* **Port Number** (e.g., block port 22/SSH)
* **Protocol** (e.g., block all UDP traffic)
* **Application layer rules** (in next-gen firewalls)

---

## ✅ Example:

**Scenario:**
You want to **block all SSH access (port 22)** from the public internet to your EC2 instance.

🔐 You create a firewall rule (in AWS it's called a **Security Group**) like:

```
Deny: 0.0.0.0/0 → port 22
Allow: 192.168.1.10 → port 22
```

Only one trusted IP can access via SSH. Others are blocked.

---

## 🧪 Real Life Analogy:

* A **firewall is like a bouncer at a club**.
  He checks:

  * Who you are (IP)
  * What you're carrying (protocol)
  * What door you're trying to enter (port)

If you're on the list (allowed), you get in. If not, you're blocked.

---


# Ingress/Inbound & Egress/Outbound
Perfect Konka! Let's simplify **Ingress vs Egress** (Inbound vs Outbound) — especially useful for interviews and cloud/networking topics.

---

## 🔁 Ingress vs Egress

| Term        | Direction                | Meaning                           | Example                                    |
| ----------- | ------------------------ | --------------------------------- | ------------------------------------------ |
| **Ingress** | Inbound to the system    | Traffic coming **into** a system  | User accessing your web app (HTTP request) |
| **Egress**  | Outbound from the system | Traffic going **out of** a system | Your app calling an external API           |

---

## 📦 In Simple Terms:

* **Ingress** = Something coming **IN**
* **Egress** = Something going **OUT**

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