
<hr style="border: 2px solid grey;">
## Learning Objectives

<div style="Border: 2px solid grey; border-radius: 15px"> 
<ul><li> Provides for data collection, storage and retrieval</li></ul>
<ul>
	 <li> Composed of:
	 <ul>
	 <li>People, hardware, software
	<li> Database, application programs, procedures
	 </ul>
</ul>
<ul> 
<li> <b>Systems Analysis:</b> process that establishes need for and extend of information systems
</ul>

<ul> 
<li><b>Systems development:</b> Process of creating information system
</ul>

</div>

<hr style="border: 2px solid grey;">

## Performance factors of an information systems

<div style="display: grid;
      grid-template-columns: 1fr 1fr;
      grid-gap: 10px; " > 

	<div style="
	width: 100%; /* Full width of the grid cell */
      aspect-ratio: 1; /* Maintain square shape */
      background-color: #3498db; /* Square color */
      display: flex;
      align-items: center;
      justify-content: center;
      color: white;
      font-size: 18px;
      font-family: Arial, sans-serif;
      padding: 10px;
      border-radius: 15px;
	"> 
		<span>Database design and implementation</span>
	</div>
	<div style="
	width: 100%; /* Full width of the grid cell */
      aspect-ratio: 1; /* Maintain square shape */
      background-color: blue; /* Square color */
      display: flex;
      align-items: center;
      justify-content: center;
      color: white;
      font-size: 18px;
      font-family: Arial, sans-serif;
      padding: 10px;
      border-radius: 15px;">
		<span>Application design and implementation</span>
	</div>
		<div style="
	width: 100%; /* Full width of the grid cell */
      aspect-ratio: 1; /* Maintain square shape */
      background-color: green; /* Square color */
      display: flex;
      align-items: center;
      justify-content: center;
      color: white;
      font-size: 18px;
      font-family: Arial, sans-serif;
      padding: 10px;
      border-radius: 15px;">
		<span>Administrative procedures</span>
	</div>
		<div style="
	width: 100%; /* Full width of the grid cell */
      aspect-ratio: 1; /* Maintain square shape */
      background-color: purple; /* Square color */
      display: flex;
      align-items: center;
      justify-content: center;
      color: white;
      font-size: 18px;
      font-family: Arial, sans-serif;
      padding: 10px;
      border-radius: 15px;">
		<span><b>Database Development:</b> Process of database design and its implementation</span>
	</div>
	

</div>

<hr style="border: 2px solid grey;">

## Systems Development Life Cycle

<div style=""> 
	<div style = "border: 2px solid grey; border-radius: 15px; padding: 15px; margin-bottom: 10px;"><span>Traces history of an information system</span></div>
	<div style = "border: 2px solid blue; border-radius: 15px; padding: 15px; margin-bottom: 10px;"><span>Provides a picture within which development are mapped out  </span></div>
	<div style = "border: 2px solid orange; border-radius: 15px; padding: 15px; margin-bottom: 10px;"><span>Iterative rather than sequential process </span></div>
</div>

<hr style="border: 1px solid grey;">

```mermaid

flowchart TD

Title[Phase]
A[Planning] --> B[Analysis] --> C[Detailed systems design]
C --> D[implementation] --> E[maintanance] --> A

```
**Planning :** 
- Initial Assessment
- Feasibility study

**Analysis:**
- User Requirement
- Logical system design

**Detailed systems design:**
- Detailed systems specification

**Implementation:**
- Coding, testing, debugging
- installation, fine-tuning

**Maintenance:**
- Evaluation
- Maintenance
- Enhancement

<hr style="border: 2px solid grey;">

## Database Life Cycle

```mermaid
flowchart TD

%% Styling for Actions
classDef actionBox stroke-width:2px,padding:20px,font-size:14px,text-align:left;
classDef PhaseBox padding:20px;


Title{Phase} --> A
A[Database initial study]:::PhaseBox
B[Database design]:::PhaseBox
C[Implementation and loading]:::PhaseBox
D[Testing and Evaluation]:::PhaseBox
E[Operation]:::PhaseBox
F[Maintenance and evolution]:::PhaseBox

Title1{Actions} --> A1
A1[
- Analyze the company situation
- Define problems
- Define objectives
- Define scope and boundaries
]:::actionBox

B1[
- Create the conceptual design
- DBMS Software selection
- Create logical design
- Create physical design
]:::actionBox

C1[
- Install DBMS
- Create Database
- Load or convert Data
]:::actionBox

D1[
- Test the database
- Fine-tune the database
- Evaluate the database
]:::actionBox

E1[
- Produce the required info flow
]:::actionBox

F1[
- Introduce changes
- Make Enhancement
]:::actionBox

F --> A
A --> B --> C --> D --> E --> F
A1 --> B1 --> C1 --> D1 --> E1 --> F1

```

<hr style="border: 1px solid grey;">

### Purpose of Database initial study

- To analyze company situation
- define problems and constraint
- define objectives
- define scope and boundaries

<hr style="border: 1px solid grey;">

### Summary of Activities in the database initial study

```mermaid

graph TD

subgraph A1
	A[Analysis of the company situation]
	B[Company operations]
	C[Company Objectives]
	D[Company Structure]
	A --> B
	A --> C
	A --> D
end

subgraph B1
	E[Definition of problems and constraints]
end

subgraph C1
	F[Database system specification]
	G[Objectives]
	H[Scope]
	J[Boundaries]
	F --> G
	F --> H
	F --> J
end

A1 --> B1 --> C1

```

<hr style="border: 2px solid grey;">

## Database Design

<div style="Border: 2px solid grey; border-radius: 15px"> 
<ul style="Background-color: pink; display: inline-block; border-radius: 10px; color: black; padding: 20px; margin-left: 15px;"> Support Company's operations and objectives</ul>
<ul style="Background-color: purple; display: inline-block; border-radius: 10px; color: white; padding: 20px; margin-left: 15px;">
	 Pointers for examining completion procedures
	 <ul>
	 <li>Data Component is an element of whole system
	<li> Database design is an iterative process
	 </ul>
</ul>
<ul style="Background-color: blue; display: inline-block; border-radius: 10px; color: white; padding: 20px; margin-left: 15px;">
Checks the ultimate final product from all perspectives
</ul>

</div>

<hr style="border: 1px solid grey;">

**Database Design Process**

```mermaid
flowchart TB

A[Conceptual Design] --> B[DBMS Selection] --> C[Logical Design]
C --> D[Physical Design]
```

1. Conceptual Design
	- Data analysis and requirement
	- ERD modelling
2. Select the DBMS
3. Logical Design
	- Map conceptual model to logical model components
	- Normalization
	- Integrity constraint
	- Validate against user requirement
4. Physical Design
	- Define data storage organisation
	- Define security and integrity
	- Define performance measures

<hr style="border: 2px solid grey;">

## Implementation and Loading

1. Install the DBMS
	- Virtualization
2. Create the Database
	- Requires the creation of the storage-related constructs
3. Load or Convert Data
	- aggregating data from multiple resources

<hr style="border: 2px solid grey;">

## Testing Factors

What to test in Database?
- physical security
- Password Security
- Access Rights
- Audits Trails
- Data Encryption
- Diskless Workstations
- Optimization


<hr style="border: 2px solid grey;">

### Levels of database Backups
- Full Backup:
	- All database object are backed up in their entirety
- Differential Backup:
	- Only modified/updated object since last full backup
- Transaction log backup
	- Only the Transactions log operation that are not reflected in previous backup are backed up

<hr style="border: 2px solid grey;">
### Sources of Database failure


<div style="border: 2px solid #444; border-radius: 15px; padding: 20px; background-color: #2e2e2e;">
  <ul>
    <li style="background-color: #3b3b3b; color: #cfcfcf; padding: 5px; border-radius: 5px; margin-bottom: 5px; border: 1px solid #555;">Software</li>
    <li style="background-color: #3b3b3b; color: #cfcfcf; padding: 5px; border-radius: 5px; margin-bottom: 5px; border: 1px solid #555;">Hardware</li>
    <li style="background-color: #3b3b3b; color: #cfcfcf; padding: 5px; border-radius: 5px; margin-bottom: 5px; border: 1px solid #555;">Programming exemptions</li>
    <li style="background-color: #3b3b3b; color: #cfcfcf; padding: 5px; border-radius: 5px; margin-bottom: 5px; border: 1px solid #555;">Transactions</li>
    <li style="background-color: #3b3b3b; color: #cfcfcf; padding: 5px; border-radius: 5px; margin-bottom: 5px; border: 1px solid #555;">External factors</li>
  </ul>
</div>

<hr style="border: 2px solid grey;">

## Periodic Maintenance Activities

- Preventive Maintenance (Backup)
- Corrective Maintenance (Recovery)
- Adaptive Maintenance
- Assignment of permissions 
- Periodic security Audits
- Periodic system-usage summaries

<hr style="border: 2px solid grey;">
## Conceptual design

- Designs a database without the database software or any physical details
- Conceptual data model - ERD, entity, attributes
- Minimum Data rule: only list what is there needed, and what needed is there

<hr style="border: 2px solid grey;">

## Conceptual Designs Steps

1. Data analysis and requirement gathering
2. ERD modelling and Normalization
3. Data model verification
4. Distribute the design


<hr style="border: 2px solid grey;">

## Iterative ER Model Verification process

```mermaid
graph TD

A[Identify central entity, Modules and component]

B[Define Process and transaction steps]

C[verify ER Model]

D{Does ER require changes?}

E[Make changes to ER model]

F(ER model verified)

A --> B --> C --> D -- no --> F
D -- yes --> E --> C


```

 <hr style="border: 2px solid grey;">

## Cohesivity and module coupling

<div style="border: 4px solid grey; border-radius: 15px; padding: 20px; font-size: 18;"> 

<li style="margin-bottom: 10px;"><b>Cohesivity:</b> Strength of the relationships among the module's entities
<li> <b>Module Coupling:</b> Extent to which modules are independent to one another

</div>

 <hr style="border: 2px solid grey;">

## Factors Affecting Software Purchasing Decision

<div style="border: 4px solid grey; border-radius: 15px; padding: 20px; font-size: 18;"> 

<li> Cost
<li> DBMS features and tools
<li> Underlying model
<li> Portability
<li> DBMS hardware requirements

</div>

