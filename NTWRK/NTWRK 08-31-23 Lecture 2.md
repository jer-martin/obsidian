#### The Internet: a "service" view:
- Infrastructure that provides services to applications
	- Web, streaming video, multimedia teleconferencing, email
- provides *programming interface* to distributed applications:
	- "hooks allowing sending/receiving apps to "connect" to, use Internet transport service
	- provides service options, analogous to postal service

- [[NTWRK 08-24-23 Lecture 1 |Protocols]] define the format and order of messages sent and received among network entities, and actions taken on message transmission and receipt 
	- (see NTWRK Lecture 1: Protocols)

	In a *time diagram,* time moves vertically. Horizontal spacing represents a spatial divide.

# A Closer Look at Internet Structure:
- #### [[NTWRK 08-24-23 Lecture 1|Network edge]]:
	- hosts: clients and servers
	- servers often in data centers

- #### Access networks: Cable access:
	- wired *and* wireless communication links
	- [[NTWRK 08-24-23 Lecture 1|frequency division multiplexing (FDM)]] 
		- (see NTWRK Lecture 1: Network Edge)
	- [[NTWRK 08-24-23 Lecture 1|hybrid fiber coax (HFC)]]
		- asymmetric: up to 40 Mbps - 1.2 Gbps downstream, 30-100 Mbps upstream
	- *network* of cable/fiber attaches homes to ISP router
		- homes *share access network* to cable headend

- #### Network core:
	- interconnected routers
	- network of networks

	[[NTWRK 08-24-23 Lecture 1|How to connect end systems to edge router?]] 
	- (see NTWRK Lecture 1: Network Edge)

- #### Access networks: Digital subscriber line (DSL):
	- uses *existing* telephone line to central office DSLAM
		- data over DSL phone line goes to Internet
		- voice over DSL phone line goes to telephone net
	- 24-52 Mbps dedicated downstream transmission rate
	- 3.5-16 Mbps dedicated upstream transmission rate

- #### Access networks: enterprise networks
	- companies, universities, etc
	- mix of wired, wireless-link
	- connects a mix of switches and routers
		- Ethernet: wired access at 100 Mbps, 1 Gbps, 10 Gbps
		- Wifi: wireless access points at 11, 54, 450 Mbps

- ## Host:
	- Sends *packets* of data
	- Host sending function
		- takes application message
		- breaks into smaller chunks, known as *packets*, of length L bits
		- transmits packet into access network at transmission rate R
			- link transmission rate, aka *link capacity*, aka *link bandwidth*

- ## Link:
	- physical media

	- #### Definitions:
		- **bit**
			- propagates between transmitter/receiver pairs
		- **physical link**
			- what lies between transmitter and receiver
		- **guided media
			- signals propagate in solid media; copper, fiber, coax
		- **unguided media
			- signals propagate freely; radio

	- #### Twisted pair (TP):
		- two insulated copper wires
			- Category 5: 100 Mbps, 1 Gbps Ethernet
			- Category 6: 10 Gbps Ethernet
				- each cable has four twisted pairs
	- #### Coaxial cable:
		- two concentric copper conductors
		- bidirectional
		- broadband
			- multiple frequency channels on cable
			- 100's Mbps per channel
	- #### Fiber optic cable:
		- glass fiber carrying light pulses, each pulse a bit
		- high speed operation
			- high speed point-to-point transmission (10's-100's Gbps)
		- low error rate
			- repeaters spaced far apart
			- immune to electromagnetic noise
	- #### Wireless radio
		- signal carried in electromagnetic spectrum
		- no physical "wire"
		- broadcast and "half-duplex"
			- sender to receiver
		- propagation environment effects:
			- reflection
			- obstruction
			- interference
		- ##### Radio Link Types
			- terrestrial microwave
				- up to 45 Mbps channels
			- Wireless LAN (Wi-Fi)
				- up to 100's Mbps
			- wide-area (e.g. cellular)
				- 4G cellular; ~10's Mbps
			- satellite
				- up to 45 Mbps per channel
				- 270 ms end-end delay
				- geosynchronous vs low-earth-orbit
