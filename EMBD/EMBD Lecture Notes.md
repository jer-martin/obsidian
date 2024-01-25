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

## SDL
- Specification and Description Language
	- Designed for specification of distributed systems
- Defined by International Telecommunication Union (ITU): Z.100 recommendation in 1980
- Provides text and GUI format
- Based on CFSM model of computation, each FSM is a process
- Uses message passing, supports ops on data

### Operations on Data
- Variables can be declared locally for processes
- Their type can be predefined or defined in SDL
- SDL supports abstract data types

### Communication in SDL
- Communication between FSMs (processes) is based on message-passing, assuming a potentially indefinitely large FIFO-queue
	- Each process fetches next entry from FIFO
	- Checks if input enables transition,
		- If yes: transition takes place
		- If np: input is ignored (exception: SAVE-mechanism)

### Process Interaction Diagrams
- Interaction between processes can be described in process interaction diagram
	- Special case of block diagrams
- In addition to processes, the diagrams contain channels and declarations of local signals

### Designation of Recipients
- Through process IDs:
	- OFFSPRING represents identifiers of processes generated dynamically
- Explicitly:
	- By including the channel name
- Implicitly:
	- If signal names imply channel names

### Hierarchy in SDL
- Process interaction diagrams can be included in blocks. Root block is called <font color="HotPink" style="font-style: italic;">system</font>
- Processes cannot contain other processes, unlike in StateCharts

### Timers
 - Timers can be deduced locally. Elapsed timers put signal into queue
 - RESET removes timer signal from queue

### Summary
- Excellent for distributed applications
	- used to specify ISDN
- Commercial tools available from SINTEF, Telelogic, Cinderella
- Not necessarily deterministic
	- Order in which FSMs are reading input is unknown
	- Not a synchronous language
- Implementation requires bound for the maximum length of FIFOs, may be difficult to compute
- Timer concept adequate for soft deadlines
- Limited programming language support
- No description of non-functional properties

## Petri Net
- Carl Adam Petri, PhD thesis, 1962
- Focus on modeling causal dependencies, no global synchro assumed (message passing only)
- Applications
	- Modeling of resources, mutual exclusion, synchro
- Key elements:
	- Conditions: met or not met
	- Events: may take place if conditions met
	- Flow relations: relates conditions and events
- Conditions, events, and the flow relation form a bipartite graph (graph with 2 types of nodes)

### Condition/Event Nets
- $N=(C,E,F)$ is called a net, if the following holds
	- $C$ and $E$ are disjoint sets
	- $F\subseteq(C\times E)\cup(E \times C)$; is a binary relation
- Definition: Let $N$ be a net and let $x \in (C\cup E)$
	- $*x:=\set{y|yFx}$ is called the set of preconditions
	- $x*:=\set{y|xFy}$ is called the set of postconditions
![center](../zassets/Pasted%20image%2020240123152055.png)

### Loops and Pure Nets
- Def: Let $(c,e)\in C\times E. \;(c,e)$ is called a loop if $cFe \wedge eFc$   
- Net $N=(C,E,F)$ is called pure if $F$ doesn't contain any loops

### Simple Nets
- A net is called simple if disjoint elements have disjoint pre and post condition sets
- Example (not a simple net):
![center](../zassets/Pasted%20image%2020240123152333.png)
- Def: Simple nets with no isolated elements meeting some additional restrictions are called condition/event nets

### Place/Transition Nets
- $(P,T,F,K,W,M_{0})$ is called a place/transition net if
	1. $N=(P,T,F)$ is a net with places $p \in P$ and transitions $t \in T$
	2. $K$: $P\rightarrow(N_{0}\cup \{\omega\})  \setminus\{0\}$
	3. $W$: $F\rightarrow(N_{0}\setminus\{0\})$ denotes the weight of graph edges
	4. $M_{0}$: $P\rightarrow N_{0}\cup\{\omega\}$
![center](../zassets/Pasted%20image%2020240123152809.png)

### Dining Philosophers
- $n>1$ philosophers sitting at a round table
- $n$ forks, $n$ plates with spaghetti
- philosophers either thinking or eating

## Predicate/Transition Nets
- Compact representation of complex systems
- Key changes
	- Tokens are becoming individuals
	- Transitions enabled if functions at incoming edges are true
	- Individuals generated by firing transitions defined through functions
- Changes can be explained by folding and unfolding C/E nets
	- semantics can be defined by C/E nets

### Summary
- Pros
	- Appropriate for distributed apps
	- Well-known theory for formally proving properties
- Cons (for the nets presented):
	- problems with modeling timing
	- no programming elements
	- no hierarchy
- Extensions:
	- extensive efforts on removing limitations

## Message Sequence Charts
- Graphical means for representing schedules; time used vertically, geographical distribution horizontally
- No distinction between accidental overlap and synchro
![center](../zassets/Pasted%20image%2020240123153549.png)

## Unified Modeling Language
- Heavy usage in UML (known as sequence diagram)
- No precise timing
- Many kinds of additional exercises
![center](../zassets/Pasted%20image%2020240123153917.png)

### State Machine Diagrams
- State machine diagrams/State diagrams:
	- UML includes variant of StateCharts
![center](../zassets/Pasted%20image%2020240123154016.png)

### Activity Diagram
- Extended Petri nets include decisions (like in flow charts)
- Graphical notation similar to SDL
![center](../zassets/Pasted%20image%2020240123154101.png)

### Deployment Diagram
- Describe execution architecture of systems (HW or SW)
	- Important for embedded systems

### Use case Diagram
- Captures typical application scenarios
![center](../zassets/Pasted%20image%2020240123154156.png)

### Package Diagram
- Represents the partitioning into packages
- Introduces hierarchy
![center](../zassets/Pasted%20image%2020240123154242.png)

### Class Diagram
- Describe object classes
![center](../zassets/Pasted%20image%2020240123154938.png)

### Timing Diagram
- Can be used to change the state of an object over time
![center](../zassets/Pasted%20image%2020240123155017.png)

### Component Diagram
- Represents components used in applications
![center](../zassets/Pasted%20image%2020240123155103.png)

## Verilog
- HW description language competing with VHDL
- Standardized:
	- IEEE 1364-1995 (Verilog version 1.0)
	- IEEE 1364-2001 (Verilog version 2.0)
- Similar features to VHDL:
	- Designs described as connected entities
	- Bit-vectors and time units are supported
- Features that are different
	- Built-in support for 4-value logic and for logic with 8 strength levels encoded in two bytes per signal
	- More features for transistor level descriptions
- Less flexible than VHDL
- More popular in US, less so in Europe (they use VHDL)

### Representation: Structural Models
- Structural models
	- Are built from gate primitives and/or other models
	- They describe the circuit using logic gates -- much as you would see in an implementation of a circuit
- Identify:
	- this is a multiplexor -- it selects one of $n$ inputs (2 here) and passes it on to the output
![center](../zassets/Pasted%20image%2020240123161216.png)

### Inside the Simulator
- A time-ordered list of events is maintained
	- <font color="HotPink" style="font-style: italic;">Event</font> - a value change scheduled to occur at a given time
	- all events for a given time are kept together
- The scheduler removes events for a given time...
	- ...propagates values, executes gate models, creates new events...
![center](../zassets/Pasted%20image%2020240123164225.png)


## VHDL
- HDL = hardware description language
- Textual HDLs replaced graphical HDLs in the 1980s (better for complex behavior)
- In this course:
	- VHDL: VHSIC hardware description language
	- VHSIC: very high speed integrated circuit

### Entities and Architectures
- Each design unit is called an entity
![center](../zassets/Pasted%20image%2020240125160912.png)
- Each architecture includes a model of the entity. By default, the most recently analyzed architecture is used. Another architecture can be requested in a configuration.

#### Entity Declaration
![center](../zassets/Pasted%20image%2020240125160956.png)
```
entity full_adder is
	port(a,b,carry_in: in Bit; -- input ports  
sum,carry_out: out Bit); --output ports  
end full_adder;
```

#### Architecture
```
architecture behavior of full_adder is  
begin  
sum <= (a xor b) xor carry_in after 10 Ns;  
carry_out <= (a and b) or (a and carry_in) or  
(b and carry_in) after 10 Ns;  
end behavior;
```
- Architectural bodies can be
	- behavioral bodies
	- structural bodies
- Bodies not referring to hardware components are called <font color="HotPink" style="font-style: italic;">behavioral bodies</font>
#### Modeling Behavior
- <font color="HotPink" style="font-style: italic;">Architecture body</font>
	- describes an implementation of an entity
	- may be several per entity
- <font color="HotPink" style="font-style: italic;">Behavioral architecture</font>
	- describes the algorithm performed by the model
	- contains:
		- process statements, each containing
		- sequential statements, including
		- signal assignment statements, and
		- wait statements

#### Behavior Example
```
architecture behav of reg4 is  
begin  
	storage : process is  
		variable stored_d0, stored_d1, stored_d2, stored_d3 : bit;  
	begin  
		if en = '1' and clk = '1' then  
			stored_d0 := d0;  
			stored_d1 := d1;  
			stored_d2 := d2;  
			stored_d3 := d3;  
		end if;  
		q0 <= stored_d0 after 5 ns;  
		q1 <= stored_d1 after 5 ns;  
		q2 <= stored_d2 after 5 ns;  
		q3 <= stored_d3 after 5 ns;  
		wait on d0, d1, d2, d3, en, clk;  
	end process storage;  
end architecture behav;
```

#### Modeling Structure
- <font color="HotPink" style="font-style: italic;">Structural architecture</font>
	- implements the model as a composition of subsystems
	- contains
		- signal declarations, for internal interconnections
			- the entity ports are also treated as signals
		- component instances
			- instances of previously declared entity/architecture pairs
		- port maps in component instances
			- connect signals to component ports
		- wait statements

#### Structure Example
![center](../zassets/Pasted%20image%2020240125161619.png)

- First declare <font color="HotPink" style="font-style: italic;">D-Latch</font> and <font color="HotPink" style="font-style: italic;">and-gate</font> entities and architectures
```
entity d_latch is  
	port ( d, clk : in bit; q : out bit );  
end entity d_latch;

architecture basic of d_latch is  
begin  
	latch_behavior : process is  
	begin  
		if clk = ‘1’ then  
			q <= d after 2 ns;  
		end if;  
		wait on clk, d;  
	end process latch_behavior;  
end architecture basic;
```
```
entity and2 is  
	port ( a, b : in bit; y : out bit );  
end entity and2;  

architecture basic of and2 is  
begin  
	and2_behavior : process is  
	begin  
		y <= a and b after 2 ns;  
		wait on a, b;  
	end process and2_behavior;  
end architecture basic;
```
- Now use them to implement a register
```
architecture struct of reg4 is  
	signal int_clk : bit;  
begin  
	bit0 : entity work.d_latch(basic)  
		port map ( d0, int_clk, q0 );  
	bit1 : entity work.d_latch(basic)  
		port map ( d1, int_clk, q1 );  
	bit2 : entity work.d_latch(basic)  
		port map ( d2, int_clk, q2 );  
	bit3 : entity work.d_latch(basic)  
		port map ( d3, int_clk, q3 );  
	gate : entity work.and2(basic)  
	port map ( en, clk, int_clk );  
end architecture struct;
```

#### Mixed Behavior and Structure
- An architecture can contain both behavioral and structural parts
	- process statements and component instances
		- collectively called <font color="HotPink" style="font-style: italic;">concurrent statements</font>
	- processes can read and assign to signals
- Example: register-transfer-level model
	- data path described structurally
	- control section described behaviorally

#### Mixed Example
![center](../zassets/Pasted%20image%2020240125162017.png)

```
entity multiplier is  
	port ( clk, reset : in bit;  
		multiplicand, multiplier : in integer;  
		product : out integer );  
end entity multiplier;  

architecture mixed of mulitplier is  
	signal partial_product, full_product : integer;  
	signal arith_control, result_en, mult_bit, mult_load : bit;  
begin  
	arith_unit : entity work.shift_adder(behavior)  // STRUCTURE
		port map ( addend => multiplicand, augend => full_product,  
			sum => partial_product,  
			add_control => arith_control );  
	result : entity work.reg(behavior)  
		port map ( d => partial_product, q => full_product,  
			en => result_en, reset => reset );  
	multiplier_sr : entity work.shift_reg(behavior)  
		port map ( d => multiplier, q => mult_bit,  
			load => mult_load, clk => clk );  
	product <= full_product;  
	control_section : process is // BEHAVIOR
		-- variable declarations for control_section  
	begin  
		-- sequential statements to assign values to control signals  
		wait on clk, reset;  
	end process control_section;  
end architecture mixed
```

#### Test Bench Example
```
entity test_bench is  
end entity test_bench;  

architecture test_reg4 of test_bench is  
	signal d0, d1, d2, d3, en, clk, q0, q1, q2, q3 : bit;  
begin  
	dut : entity work.reg4(behav)  
		port map ( d0, d1, d2, d3, en, clk, q0, q1, q2, q3 );  
	stimulus : process is  
	begin  
		d0 <= ’1’; d1 <= ’1’; d2 <= ’1’; d3 <= ’1’; wait for 20 ns;  
		en <= ’0’; clk <= ’0’; wait for 20 ns;  
		en <= ’1’; wait for 20 ns;  
		clk <= ’1’; wait for 20 ns;  
		d0 <= ’0’; d1 <= ’0’; d2 <= ’0’; d3 <= ’0’; wait for 20 ns;  
		en <= ’0’; wait for 20 ns;  
		...  
		wait;  
	end process stimulus;  
end architecture test_reg4;
```

### Summary
- Behavioral hierarchy (procedures & functions)
- Structural hierarchy but no nested processes
- No specification of non-functional properties
- No object-orientation
- Static number of processes
- Complicated simulation semantics
- Too low level for initial specification
- Good for intermediate language for hardware generation

## SystemC
### Motivation
- Many standards (e.g. the GSM and MPEG-standards) are published as C programs
	- Standards have to be translated if special hardware description languages have to be used
- The functionalities of systems are provided by a mix of hardware and software components
	- Simulations require an interface between hardware and software simulators unless the same language is used for the description of hardware and software

### Required Features
- Requirements and solutions for modeling HW in a SW language:
- C++ class library including required functions
- Concurrency: via processes, controlled by sensitivity lists and calls to wait primitives
- Time: Floating point numbers in SystemC 1.0 and Integer values in SystemC 2.0; units ps, ns, $\mu$s, etc
- Support of bit-datatypes: bitvectors of different lengths; multiple-values logic (2 and 4; resolution)
- Communication: plug and play channel model, allowing easy replacement of intellectual property
- Deterministic behavior not guaranteed

### HelloWorld
```
#include <systemc .h>  
#include <iostream>  

SC _MODULE( hello ) {  
	void say_hello () {  
	cout << " hello " << name () << endl ;}  
	SC_CTOR( hello ) {  
	SC THREAD( say_hello );}  
};  
int sc_main ( int argc , char ** argv ) {  
	hello hello_inst (" world ");  
	sc_start ();  
}
```

## System Verilog
- Corresponds to Verilog versions 3.0 and 3.1.
- Includes:  
	- Additional language elements to model behavior  
	- C data types, such as int. Type definition facilities  
	- Definition of interfaces of hardware components as separate entities  
	- Mechanism for calling C/C++-functions from Verilog  
	- Limited mechanism for calling Verilog functions from C.  
	- Classes can be used in testbenches.  
	- Dynamic process creation.  
	- Standardized inter-process communication and synchronization including semaphores.
	- Automatic memory allocation & deallocation.  
	- Language features providing interface for formal verification.

## Other Languages
- MATLAB (Matrix Laboratory)
- Simulink
- Esterel

## Basic Design Methodology
![center](../zassets/Pasted%20image%2020240125164415.png)

## Levels of Hardware Modeling
- System level
- Algorithmic level
- Instruction set level
- Register-transfer level (RTL)
- Gate-level models
- Transistor-level models
- Layout models
- Process and device models

### System level
- The term system level is not clearly defined
- It is used here to denote the entire embedded system and possibly also the environment
- Such models may include mechanical as well as information processing aspects, and may be difficult to find appropriate simulators. Solutions include VHDL-AMS, SystemC or MATLAB. MATLAB and VHDL-AMD support modeling partial differential equations.
- Challenge to model information processing parts of the system in such a way that the simulation model can also be used for the synthesis of the system

### Algorithmic level
- Simulating the algorithms that we intend to use within the embedded system
- No reference is made to processors or instruction sets
- Data types may still allow a higher precision than the final implementation
- If data types have been selected such that every bit corresponds to exactly one bit in the final implementation, the model is said to be bit-true. Translating non-bit-true into bit-true models should be done with tool support
- May consist of single processes or of sets of cooperating processes

#### MPG-4 Full Motion Search
```
for (z=0; z<20; z++)  
	for (x=0; x<36; x++) {x1=4*x;  
		for (y=0; y<49; y++) {y1=4*y;  
			for (k=0; k<9; k++) {x2=x1+k-4;  
				for (l=0; l<9; ) {y2=y1+l-4;  
					for (i=0; i<4; i++) {x3=x1+i; x4=x2+i;  
						for (j=0; j<4;j++) {  
							y3=y1+j; y4=y2+j;  
							if (x3<0 || 35<x3||y3<0||48<y3)  
								then_block_1;  
							else else_block_1;  
							if (x4<0|| 35<x4||y4<0||48<y4)  
								then_block_2;  
							else else_block_2;  
}}}}}}
```

#### Instruction level
- Algorithms have already been compiled for the instruction set of the processor(s) to be used
- Simulations at this level allow counting the executed amount of instructions
- Variations
	- Simulation only the effect of the instructions
	- Transaction-level modeling: each read/write is one transaction, instead of a set of signal assignments
	- Cycle-true simulations: exact number of cycles
	- Bit-true simulations: simulations using exactly the correct number of bits

#### Register Transfer Level (RTL)
- At this level, we model all the components at the register-transfer level, including
	- arithmetic/logic units (ALUS)
	- registers
	- memories
	- muxes
	- decoders
- Models at this level are always cycle-true
- Automatic synthesis from such models is not a major challenge

### Gate-level
- Models contain gates as the basic components
- Provide accurate information about signal transition probabilities and can therefore also be used for power estimations
- Delay calculations can be more precise than for the RTL. Typically no information about the length of wires (still estimates)
- Term sometimes also used to denote Boolean functions (No physical gates; only considering the behavior of the gates). Such models should be called “Boolean function models”.

### Transistor-level
- Transistor (switch) level models use switches (transistors) as their basic components.  
- Transistor level models use digital value models.  
- In contrast to gate-level models, transistor level models are capable of reflecting bidirectional transfer of information.  
- Models circuit theory and its components (current and voltage sources, resistors, capacitances, inductances, ...) form the basis of simulations.  
- Simulations involve partial differential equations.

### Layout-level
- Reflects the actual circuit layout, includes geometric information
- Cannot be simulated directly: behavior can be deduced by correlating the layout model with a behavioral description at a higher level or by extracting circuits from the layout
- Length of wires and capacitances frequently extracted from the layout, back-annotated to descriptions at higher levels (more precision for delay and power estimations)

## Conclusion
- Important to capture the behavior of a system using a suitable specification language
	- Enables automated analysis, synthesis, verification, etc.
- Explored various specification languages
	- Petri Nets enable nondeterministic computation
	- VHDL/Verilog are used for specifying hardware
	- UML and SystemC are used for specifying systems (hardware, software, constraints, etc)
- Design and verification complexity increases with behavior at different abstraction levels
	- Algorithm, RTL, gate, transistor, layout, etc.

