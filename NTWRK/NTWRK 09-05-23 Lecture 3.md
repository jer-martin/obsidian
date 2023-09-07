## Packet Switching
- #### Store and Forward
    - Transmission Delay
        - Takes $L/R$ seconds to transmit $L$-bit packet into link at $R$ bps
    - End-End Delay
        - $2L/R$, assuming zero propagation delay
    - entire packet must arrive at router before it can be transmitted

- #### Queueing Delay, Loss
    - if arrival rate (in bps) to link exceeds transmission rate (bps) of link for a period of time
        - packets will queue, waiting to be transmitted on output link
        - packets can be dropped (lost) if memory buffer in router fills up

- #### Two Key Network-core Functions
    - Forwarding
        - Local action
        - move arriving packets from router’s input link to appropriate router output link
    - Routing
        - Global action
        - determine source-destination paths taken by packets
        - routing algorithms

## Circuit Switching
- end-end resources allocated to, reserved for "call" between source and destination
- dedicated resources (no sharing)
    - circuit-like (guaranteed) performance
- circuit segment idle if not used by call (no sharing)
- commonly used in traditional telephone networks

- #### Frequency Division Multiplexing (FDM)
    - optical, electromagnetic frequencies divided into (narrow) frequency bands
    - each call allocated its own band, can transmit at max rate of that band


- #### Time Division Multiplexing (TDM)
    - time divided into slots 
    - each call allocated periodic slots
    - can transmit at maximum rate of frequency band
        - only during time slot

![](../zassets/Pasted%20image%2020230907140812.png)

## Packets V.S. Circuits
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
- #### What happens if > 35 users?
