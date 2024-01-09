# Embedded Systems
# Overview
## Two Types of Computing
- Desktop / Laptop / Server - produced millions / year
- Embedded and cyber-physical systems - billions / year
### Embedded Systems are the future!
- Automobiles, entertainment, communication, aviation, medical...
- Internet of Things (IoT), Cyber-Physical systems
## Components of Embedded Systems
![center](../zassets/Pasted%20image%2020240109151425.png)

### Analog Components
- Sensors, Actuators
#### Digital Components
- Processor, Coprocessors, Memories, Buses
- Controllers, Application specific hardware
### Converters
- Analog-to-digital (A2D), D2A...
### Software
- Operating systems
- Middleware
- Applications (MPEG-x, GSM-kernel, ...)

# Fundamentals
## Characteristics
#### Application Specific
- Applications are known a priori
- Optimize for cost, area, power, and performance
#### Digital Signal Processing
- Signals are represented digitally
#### Reactive
- Reacts to changes in the system's environment
#### Real-Time
- Compute certain tasks before deadline
#### Reliability
- Probability of system working correctly provided that it was working at t=0
#### Maintainability
- Probability of system working correctly $d$ time units after error occurred
#### Safety
- Not harmful for user
#### Security
- Confidential and authentic communication
### Traditional Design Challenges
- Low cost
- Light weight
- Reliability
- Low power
- Portable
- Complexity
- Ease of Use
- Security
- Digital/analog requirements
- Shrinking time-to-market
- Short product lifetime
- Real-time processing
- Inherent concurrency
- HW/SW co-design
- Network friendly
# Major Challenges
## Low Power
*Power is a problem!*
![center](../zassets/Pasted%20image%2020240109153431.png)

$$E = \int P\;dt$$
- In many cases, faster execution means less energy, but the opposite may be true if power has to be increased to allow faster execution

### Reducing Energy Consumption
![center](../zassets/Pasted%20image%2020240109154258.png)

- Infrared Cameras (FLIR) can be used to detect thermal distribution

#### Dynamic Power Management
- <font style="color:red">RUN</font>: operational
- <font style="color:red">IDLE</font>: a SW routine may stop the CPU when not in use, while monitoring interrupts
- <font style="color:red">SLEEP</font>: full shutdown of on-chip activity

#### Dynamic Voltage Scaling (DVS)
- $E = P \times T$
- $P \propto V^{2}$
	- E (energy), P (power), T (time), V (voltage)
- Example:
	- A task is given with workload W and deadline D. Assume that idle energy is negligible.
![center](../zassets/Pasted%20image%2020240109155254.png)




