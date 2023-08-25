## Protocols and Algorithms
- [[ALGO 08-24-23 Lecture 1|Algorithms]]: formal procedure to accomplish some task
- Protocol: governs information exchange and collective behavior of distributed entities
	- For certain tasks

### Chapter 1
#### Goal: 
- Get "feel", "big picture"

#### Overview:
- What *is* the internet?
- What *is* a protocol?
- **Network Edge**: hosts, access network, physical media
- **Network Core**: packet/circuit switching, internet structure
- **Performance**: loss, delay, throughput
- Security

#### The Internet: a "nuts and bolts" view
- Billions of connected computing devices
	- **Hosts** = end systems
	- running network apps at internet's "edge"
- **Packet Switches**: forward packets (chunks of data)
	- routers, switches
- **Communication Links**:
	- fiber, copper, radio, satellite
	- transmission rate: *bandwidth*
- Networks
	- collection of devices, routers, links
	- managed by an organization
- The internet is a "network of networks"
	- Interconnected ISPs
- Protocols are everywhere:
	- control sending and receiving of messages
	- e.g. HTTP, Skype, TCP, 4G, Ethernet
- Internet standards
	- RFC: Request for Comments
	- IETF: Internet Engineering Task Force

#### What is a protocol?
- Human protocols:
	- Whats the time?
	- I have a question
	- introductions
- Network protocols:
	- Computers rather than humans
	- all communication activity in Internet governed by protocols

**Protocols define the format, order of messages sent and received among network entities, and actions taken on message transmission, receipt**

### Network edge:
- hosts: clients and servers
- servers are often in data centers
Access networks, physical media:
- Wired, wireless comm links

How do you connect end systems to edge router?
- residential access nets
- institutional access nets
- mobile access nets
When connected, what do we look for?
- transmission rate (bit/s)
- shared or dedicated access among users?

*Network of cable/fiber attaches homes to ISP router*

**Frequency division multiplexing (FDM):**
- different channels transmitted in different frequency bands

**Hybrid Fiber-Coax (HFC):**
- asymmetric: up to 40 Mbps - 1.2 Gbps downstream, 30-100 Mbps upstream
