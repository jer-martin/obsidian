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
## Major Challenges
### Low Power
*Power is a problem!*
![center](../zassets/Pasted%20image%2020240109153431.png)

$$E = \int P\;dt$$
- In many cases, faster execution means less energy, but the opposite may be true if power has to be increased to allow faster execution

#### Reducing Energy Consumption
![center](../zassets/Pasted%20image%2020240109154258.png)

- Infrared Cameras (FLIR) can be used to detect thermal distribution

##### Dynamic Power Management
- <font style="color:red">RUN</font>: operational
- <font style="color:red">IDLE</font>: a SW routine may stop the CPU when not in use, while monitoring interrupts
- <font style="color:red">SLEEP</font>: full shutdown of on-chip activity

##### Dynamic Voltage Scaling (DVS)
- $E = P \times T$
- $P \propto V^{2}$
	- E (energy), P (power), T (time), V (voltage)
- Example:
	- A task is given with workload W and deadline D. Assume that idle energy is negligible.
![center](../zassets/Pasted%20image%2020240109155254.png)

### Design Complexity
- <font color="HotPink" style="font-style: italic;">Moore's Law</font> - exponential growth; transistors double every couple of years
#### Technology and Demand
![center](../zassets/Pasted%20image%2020240116150649.png)

##### Who wants to be a millionaire?
- Starting investment is <font style="color:red">one cent</font>.
- Double it every day
	- 20 days - 1 million cents
	- 27 days - millionaire
	- 37 days - billionaire
- Doubling transistors every 18 months becomes hard to imagine
- Believe it or not, each of us has more than a million ancestors in the last 20 generations

#### Verification Complexity
- ASIC/SOC <font color="HotPink" style="font-style: italic;">respin</font> is when there is a problem with a chip and the chip needs to be rebuilt
- The success rate for new silicon is dropping - 48% 1st silicon success in 1999, versus 39% in 2004
- 71% of SOC re-spins are due to logic bugs
![center](../zassets/Pasted%20image%2020240116151152.png)

### Time-To-Market
- Many devices are built on aggressive schedules: 1 year for exploration and planning, then 3-4 years for development and production
- <font color="HotPink" style="font-style: italic;">Time-To-Market</font> is the time required to develop a product to the point it can be sold to consumers
- <font color="HotPink" style="font-style: italic;">Market Window</font> is the period during which the product will have the highest sales
- Average TTM constraint is about 8 months
- Delays can be costly
#### Losses due to Delayed Market Entry
- Simplified revenue model
	- Product live = 2W, peaks at W
	- **Revenue** = area of the triangle
	- **Loss** = difference between on-time and delayed triangle areas (shaded region)
![center](../zassets/Pasted%20image%2020240116151647.png)
- Area  = $\frac{1}{2}\times\text{base}\times\text{height}$
	- On-time = $\frac{1}{2}*2W* W$
	- Delayed = $\frac{1}{2}*(2W-D)*(W-D)$
- Percentage revenue loss = $D\frac{3W-D}{2W^{2}}* 100\%$
##### Examples
- Lifetime 2W = 52 weeks, delay D = 4 weeks, loss = $\left(4 * \frac{3 * 26 - 4}{2*26^{2}}\right)* 100\% = 22\%$
- Lifetime 2W = 53 weeks, delay D = 10 weeks, loss = $(10 * \frac{3*26-10}{2*26^{2}})*100\%=50\%$

#### Design Productivity Gap
![center](../zassets/Pasted%20image%2020240116152204.png)

- 1981 leading edge chip required 100 man-months
	- 10,000 transistors / 100 transistors/month
- 2002 leading edge chip requires 30k man-months
	- 150,000,000 / 5000 transistors/month
- Designer cost increase from $1M to $300M
##### Mythical Man-Month
- In theory, adding designers to team reduces project completion time
- In reality, productivity per designer decreases due to team management complexity and communication overhead
- In the software community, known as the <font color="HotPink" style="font-style: italic;">"mythical man-month"</font> (Brooks, 1975)
- At some point, can actually lengthen completion time!
![center](../zassets/Pasted%20image%2020240116152504.png)

### Security and Reliability
#### Putting Computing In Everyones Hands
- Too many opportunities to attack
- Users less savvy/caring of system internals and vulnerabilities
*How to minimize vulnerability to malicious attacks of diverse and complex computing?*
- Especially in the hands of naive users
#### Mobile Devices: Attack Surface
- Attacks on privacy via malicious apps and in-app ad libraries
- Premium-rate services
- hardware attacks
- browser attacks
- mobile network attacks
- sensor malware exploit
- mobile cloud apps malware
#### Attacks on Embedded Systems
- Remote software (worm, trojan, virus)
- Priority based passive hardware attacks (power or EM analysis)
- Reversible active proximity-based attacks (fault injectors)
- Irreversible hardware attacks (tampering)
*Fakes make this easier to do*

## Specification
- Provide a clear and unambiguous description of the system functionality
- Support different models of computations
	- Petri Nets, FSMs, Data Flow Models...
- Should not constrain implementation options
- Enable computer-aided analysis techniques
	- Estimation and exploration
	- Partitioning
	- Synthesis
	- Validation
### Requirements for Specification
##### Hierarchy
- Humans are not capable of understanding systems containing more than ~5 objects
	- Behavioral hierarchy
		- states, processes, procedures
	-  Structural hierarchy
		- processors, printed circuit boards
##### Timing behavior
##### State-oriented behavior
- required for reactive systems
##### Event-handling
- external or internal events
##### Support for the design of dependable systems
- Unambiguous semantics
##### Exception-oriented behavior
- Not acceptable to describe exception in each state
##### Concurrency
- Real life systems are concurrent
##### Synchronization and communication
- Components needs to communicate
##### Presence of programming elements
- Arithmetic operations, loops, and function calls
##### Executability
- No algebraic specification
##### Support for the design of large systems
##### Domain-specific support
##### Readability
##### Portability and flexibility
##### Termination
- It should be clear, at which time all computations are completed
##### Support for non-standard I/O devices
- Direct access to switches, displays,...
##### Non-functional properties
- Fault tolerance, disposability, EMC-properties, weight, size, user friendliness, extendability, expected life time, power consumption

# Modeling vs Specification
- Modeling (or models of computation) is the underlying formalism to represent the system
	- For example: FSM, Graph Model
- Specification is performed using a language that supports the model of computation
	- Specification language is only a syntactic sugar, does not add any new representation capability.
		- For example, a language that is designed for capturing graph-based models, can only capture nodes & edges
	- Sequential computation supported by C/C++/Java
	- Parallel computation supported by VHDI/Verilog

## Finite State Machine
- Traffic light controller
	- Traffic sensors: $T_{a}, T_{b}$ (True when there's traffic)
	- Lights: $L_{a},L_{b}$ 
![center](../zassets/Pasted%20image%2020240118161947.png)

![center](../zassets/Pasted%20image%2020240118162033.png)

## Control and Data Flow Graph
- Commonly used to model program structure
![center](../zassets/Pasted%20image%2020240118162144.png)

![center](../zassets/Pasted%20image%2020240118162157.png)

## Task Graph
- Used to model multi-rate systems
![center](../zassets/Pasted%20image%2020240119104523.png)

## More Examples
- Communicating finite state machines (CFSMs)
![center](../zassets/Pasted%20image%2020240119104636.png)
- Discrete event model
![center](../zassets/Pasted%20image%2020240119104656.png)
- Differential Equations
$$\frac{\delta^{2}x}{\delta t^{2}}=b$$
- Asynchronous message passing
![center](../zassets/Pasted%20image%2020240119104738.png)
- Synchronous message passing
![center](../zassets/Pasted%20image%2020240119104751.png)

## State Charts
- FSM will be in exactly one of the substates of S if S is active (either in A or in B or...)
![center](../zassets/Pasted%20image%2020240119104921.png)
- S is the superstate, A B C D E are substates

### Concurrency
- Convenient way of describing concurrency
- AND-super states: FSM is in all (immediate) sub-states of a superstate
![center](../zassets/Pasted%20image%2020240119105922.png)
### Timers
- Timer needs to be modeled
- StateCharts uses special edges for timeouts
- **If event a does not happen while the system is in the left state for 20 ms, a timeout will take place.**
![center](../zassets/Pasted%20image%2020240119105107.png)
##### Example
- Timer for an answering machine
![center](../zassets/Pasted%20image%2020240119105126.png)
### Simulation Phases
- Three phases:
	1. Effect of external changes on events and conditions is evaluated
	2. The set of transitions to be made in the current step and right hand sides of assignments are computed
	3. Transitions become effective, variables obtain new values
- Separation into phases 2 and 3 guarantees deterministic and reproducible behavior
##### Example
![center](../zassets/Pasted%20image%2020240119105340.png)
- In phase 2, variables a and b are assigned to temporary variables. In phase 3, these are assigned to a and b. As a result, variables a and b are swapped.
- In a single phase, executing the left state first would assign the old value of b (=0) to a and b. Executing the right state first would assign the old value of a (=1) to a and b. The execution would be non-deterministic.
### Reflects Model of Clocked Hardware
- In an actual clocked (synchronous) hardware system, both registers should be swapped
- Same separation into phases found in other languages as well, especially those that are intended to model hardware
![center](../zassets/Pasted%20image%2020240119110403.png)

### Broadcast Mechanism
- Values of variables are visible to all parts of the StateCharts model
- New values become effective in phase 3 of the current step and are obtained by all parts of the model in the following step
- StateCharts implicitly assumes a broadcast mechanism for variables
- StateCharts is appropriate for local control systems, but not for distributed applications for which updating variables may take some time

### Evaluation of StateCharts
- Pros:
	- Hierarchy allows nesting of AND/OR-superstates
	- Large number of commercial simulation tools available (StateMate, StateFlow, BetterState...)
	- Back-end tools translate StateCharts into C or VHDL - enabling hw/sw implementations
- Cons:
	- Generated C programs frequently inefficient
	- Not useful for distributed applications
	- No programs construct
	- No description of structural hierarchy

## General Language Characteristics
### Synchronous vs. Asynchronous Languages
- Synchronous languages describe concurrently operating automata
- Synchronous languages aim at providing high level, modular constructs to make design of such automaton easier \[Halbwachs]
- Synchronous languages implicitly assume the presence of a (global) clock. Each tick, all inputs are considered, new outputs and states are calculated and the transitions are made
	- Requires broadcast mechanism
	- StateCharts is synchronous

### Communication Paradigms
- Message passing
	- Non blocking communication
		- Sender does not have to wait until message has arrived
		- Potential buffer overflow
	- Blocking communication
		- Sender will have to wait until receiver has received message
		- Explicit ACK from receiver required
		- Receiver can check before sending ACK
- Shared memory
	- Critical sections = sections at which exclusive access to some resource $r$ must be guaranteed
	- StateCharts uses shared memory

### Timing Specification
- Four types of timing specs required \[Burns, 90]
	- Measure elapsed time
		- Check how much time has elapsed since last call
	- Means for delaying processes
	- Possibility to specify timeouts
		- We would like to control state
	- Methods for specifying deadlines
		- With current languages not available or specified in separate control file
- StateCharts comprises a mechanism for specifying timeouts
	- Other types of timing spec not supported

