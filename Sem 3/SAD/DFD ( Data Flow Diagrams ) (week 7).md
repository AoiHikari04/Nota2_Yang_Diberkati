
<hr style="border: 2px solid grey;" >

## What is DFD??

- shows how data moves through an information system.
- provide logical model that show **what** does the system do, not **how**
to do it
- DFD use various symbols to show the systems functionality

<hr style="border: 2px solid grey;" >

## Symbols DFD

![[Pasted image 20250123151456.png]]

- **Symbols:**
	- Represents one or more data items. 
	- Show the general functionality of the process (e.g. process/data flow/ data store etc.)
	- Must have a process symbol on at least one end of the data flow(arrow symbol)

example:

![[Pasted image 20250123151742.png]]



## Data Flow and Process must avoid

- **Spontaneous Generation**
	- No input data flow
- **Black Hole** 
	- Produces no output data flow
- **Gray Hole**
	- Has at least one input and one output but the input is not enough to create the output
	- insufficient input
	- input x cukup


<hr style="border: 2px solid grey;" >

## Symbols for Data Store

![[Pasted image 20250123152247.png]]

- Flat rectangle that is open on the right side and closed on the left side
- Identifies the data it contains

**Use for:**
- Represent data the systems store because one or more process need to use data later
- Represent a file or part of database
- Must be connected to a process
- Must have at least one incoming or outgoing data flow

Examples:
![[Pasted image 20250123152531.png]]



<hr style="border: 2px solid grey;" >

## Symbols for Entity

![[Pasted image 20250123152733.png]]

- Rectangle, which may be shaded
- Name of the entity inside the square

**Use For:**
- Shows the external entities that provide data to the systems or receive the outputs
- The beings that give inputs or accept output

**Reminder:**

- **Entity**: A person, place, thing which data is collected and maintained
- **External Entity:** Outside the system boundary but supplies input or accepts output

**Rules**
- Entity must be connected to a process by a dataflow
- must not be directly connected to data flow or other entity

![[Pasted image 20250123154031.png]]

<hr style="border: 2px solid grey;" >

## Creating a set of DFDs

**Three-step Process**
- Step 1: Draw a context diagram
	- Represents the entire information system but does not show the internal workings
- Step 2: Draw a diagram 0 DFD
	- describe the next level of detail inside context diagram which will reveal additional process
- Step 3: Draw the lower-level diagrams
	- Describe the next level of detail inside process in diagram 0

**Guidelines for DFDs**
- Draw the context diagram so that it fits one page
- Use the information systems name as the process name
- Unique name for each symbols
- Do not cross Line in Data flow
- Provide Unique name for systems


<hr style="border: 1px solid grey;" >

### Step 1: draw a context diagram

- is a top level view of an information system 
- Symbolize all processing activity within a system with a single process symbol; **Process 0**

![[Pasted image 20250123170105.png]]

**Rules for creating context Diagram**
- Placing a single process symbol at the center, name it process 0, and gives it a system name
- place external entites and use data flow to connect them
- do not show any data stores inside the system
- create a lebeled input and output between entities and central system

<hr style="border: 1px solid grey;" >

### Step 2: draw a diagram 0 DFD

- zooms in system to shows major internal process, data flows and data stores
- Repeats the entities and data flow from context diagram
- must retain all connections from context diagram
- Diagram 0 is an exploded view of process 0

![[Pasted image 20250123205138.png]]

**Rules for creating Diagram 0 DFD**

- each process has a reference number
- the process number do not suggest the process is in sequential order

**Functional Primitive:**
- Is a process that consists of a single function that is not exploded further
- document the logic in the data dictionary

<hr style="border: 1px solid grey;" >

### Step 3: Draw the Lower-Level diagrams

- Must use leveling and balancing techniques

**Leveling examples:**
- Also called exploding, partitioning or decomposing
- uses serires of increasing detailed DFDs untill all propcess are identified as functional primitives (cannot be detailed further)
**Balancing examples:**
- Ensures that the input and output are the same

