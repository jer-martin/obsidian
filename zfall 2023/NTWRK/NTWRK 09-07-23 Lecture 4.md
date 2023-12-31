## Packets V.S. Circuit
*packet switching allows more users to use the network!*
### Example:
- 1 Gb/s link
- each user:
    - 100 Mb/s when active
    - active 10% of the time
- #### How many users can the network support?
    - **circuit switching**
        - 10 users
    - **packet switching**
        - with 35 users, probability > 10 active at same time is less than .0004 *

- #### How did we get value .0004?
	- Binomial Distribution ($n = 35, x = 11, p = 0.1, P(X\ge x)$)
- #### What happens if > 35 users? 
	- the P value goes up

#### Is packet switching the "slam dunk winner"?
- great for bursts of data
	- resource sharing
	- simpler, no call setup
- excessive congestion possible
	- packet delay and loss due to buffer overflow
	- protocols needed for reliable data transfer, congestion control
- how to provide circuit-like behavior?
	- bandwidth guarantees traditionally used for audio/video applications


## Internet Structure: A "network of networks"
- Hosts connect to Internet via *access* Internet Service Providers (ISPs)
	- residential, enterprise, (company, university, commercial) ISPs
- Access ISPs in turn must be interconnected
	- so that any two hosts can send packets to each other
	- resulting network of networks is very complex

	*Question: given **millions** of ISPs, how to connect them?*
	- connecting each ISP to each other *directly* doesn't scale
		- $O(n^{2})$ connections
	
	*Option: connect each ISP to one global transit ISP?*
	- customer and provider ISPs have economic agreement
	- if there is one global ISP, there will be competitors... who also want to be connected
		- regional networks may arise to connect access nets to ISPs

![](../zassets/Pasted%20image%2020230907143352.png)

 - content provider networks (Google, Microsoft, Akamai) may run their own network to bring services and content closer to end users

![](../zassets/Pasted%20image%2020230907143435.png)

- At the "center" is a small number of well-connected large networks
	- "tier 1" commercial ISPs (Sprint, AT&T), national & international coverage
	- content provider networks (Google, Meta), private network that connects it's data centers to the Internet
		- often bypasses regional (tier 1) ISPs

## How do packet loss and delay occur?
- Packets queue in router buffers
	- they queue, wait for turn
	- arrival rate to link (temporarily) exceeds output capacity: packet loss

- ##### Transmission Delay $d_{trans} = L/R$
	- packet being transmitted
	- L: packet length (bits)
	- R: link transmission rate (bps)
- ##### Queueing Delay $d_{queue} = La/R$
	- packets in buffers
	- time waiting at output link for transmission
	- R: link bandwidth (bps)
	- L: packet length (bits)
	- a: average packet arrival rate
	- **Averages:**
		- $\frac{La}{R}\approx0$ 
			- avg. queueing delay small
		-  $\frac{La}{R} → 1$ 
			- avg. queueing delay large
		- $\frac{La}{R} > 1$
			- more "work" arriving than can be serviced
			- avg. queueing delay $\infty$
- ##### Processing Delay $d_{proc}$
	- check bit errors
	- determine output link
	- typically < msec
- ##### Propagation Delay $d_{prop} = d/s$
	- d: length of physical link
	- s: propagation speed


- ##### Nodal Delay
	- $d_{nodal}= d_{proc}+ d_{queue}+ d_{trans}+ d_{prop}$


- #### Throughput
	- rate (bits / time unit) at which bits are being sent from sender to receiver
		- instantaneous
			- rate given at a point in time
		- average
			- rate over longer period of time
