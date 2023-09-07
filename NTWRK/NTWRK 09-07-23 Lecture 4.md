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
- Hosts connect to Internet via accessing Internet Service Providers (ISPS)