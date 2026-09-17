 MATATU TERMINUS SCHEDULER
LAB 2
Lua
GROUP 23 MEMBERS
Bruce kariti   C026-01-0969/2025
Kelvin musina  C026-01-0946/2025
Allan chesipul C026-01-0947/2025
I. INTRODUCTION
The Matatu Terminus Scheduler is a Lua programming project designed to demonstrate the use of Lua coroutines and cooperative scheduling.

The system models four matatu routes and manages passenger boarding, waiting passengers, and route departures.

The four routes are:

Rongai
Thika
Ngong
Kitengela
Each route maintains its own passenger and waiting state and is managed using a coroutine.

II. PROBLEM STATEMENT
A busy matatu terminus may have several routes operating continuously.

The project demonstrates how Lua coroutines can be used to manage different routes while allowing the routes to share execution through cooperative scheduling.

The scheduler processes each route in a round-robin sequence.

III. OBJECTIVES
The objectives of the system are to:

Demonstrate Lua coroutines.
Create a coroutine for each route.
Manage passenger boarding.
Track waiting passengers.
Determine when a matatu should depart.
Demonstrate cooperative scheduling.
Demonstrate round-robin scheduling.
Check coroutine status.
Handle coroutine execution errors.
Display the final state of each route.
IV. ROUTE DATA
The system contains four routes:

Rongai
Thika
Ngong
Kitengela
Each route begins with:

Passengers = 0
Waiting = 0
Each route is represented using a Lua table.

V. ROUTE COROUTINES
A coroutine is created for every route using the route coroutine creation function.

The coroutine continuously waits for a command from the scheduler.

The coroutine uses:

coroutine.yield()

to pause its execution and return control to the scheduler.

The scheduler can later resume the coroutine and provide a command.

VI. BOARD COMMAND
When a route receives the "board" command:

The passenger count increases by 1.
The waiting count is reset.
The current passenger state is displayed.
The operation represents a passenger boarding a matatu on the selected route.

VII. WAIT COMMAND
When a route receives the "wait" command:

The waiting count increases by 1.
The current waiting cycle is displayed.
This represents a route waiting for additional passengers or another scheduling opportunity.

VIII. DEPARTURE CONDITIONS
A route can depart under two conditions.

Condition 1: Passenger Capacity
A route departs when:

Passengers >= 8

When this happens:

A departure message is displayed.
Passenger count is reset to 0.
Waiting count is reset to 0.
Condition 2: Waiting Condition
A route also departs when:

Waiting > 3

AND

Passengers >= 5

After departure, both passenger and waiting counts are reset.

IX. COROUTINE MANAGEMENT
The system creates a separate coroutine for each route and stores the coroutines in a route-coroutine collection.

The status of a coroutine is checked using:

coroutine.status()

A coroutine is resumed using:

coroutine.resume()

The coroutine can yield control using:

coroutine.yield()

These operations allow the scheduler to control the execution of each route.

X . ROUND-ROBIN SCHEDULING
The scheduler uses a round-robin approach.

The routes are processed in the following order:

Rongai ↓ Thika ↓ Ngong ↓ Kitengela ↓ Rongai ↓ ...

After Kitengela is processed, the scheduler returns to Rongai.

This allows every route to receive an opportunity to execute.

XI . SCHEDULING LOGIC
The scheduler maintains the current route.

For every scheduling cycle, the scheduler checks the passenger count.

If:

Passengers < 5

the scheduler sends:

"board"

If:

Passengers >= 5

the scheduler sends:

"wait"

The selected command is then sent to the route coroutine.

XII . COROUTINE RESUMING
The scheduler resumes a route coroutine using:

coroutine.resume(co, command)

The result of the resume operation is checked.

If an error occurs, the program reports the error together with the relevant route information.

XIII. COOPERATIVE SCHEDULING
The project demonstrates cooperative scheduling.

A route coroutine does not continue executing indefinitely. Instead, it uses coroutine.yield() to voluntarily return control to the scheduler.

The scheduler can then resume another route.

This allows multiple route processes to share execution.

XIV . NUMBER OF SCHEDULING CYCLES
The scheduler is executed for 40 cycles using:

scheduler(40)

During these cycles, the routes are processed in round-robin order.

After the 40 cycles are completed, the final state of every route is displayed.

IV . LUA PROGRAMMING CONCEPTS DEMONSTRATED
Tables
Lua tables are used to store route information and route states.

Functions
Functions are used to organize the route and scheduler operations.

Coroutines
Coroutines are the main programming language concept demonstrated by the project.

coroutine.create()
Creates a coroutine for a route.

coroutine.resume()
Resumes a suspended coroutine and sends it a command.

coroutine.yield()
Suspends the coroutine and returns control to the scheduler.

coroutine.status()
Checks the current state of a coroutine.

Cooperative Scheduling
The route coroutines cooperate with the scheduler by yielding control.

Round-Robin Scheduling
The scheduler processes each route in sequence and repeatedly cycles through all routes.

Error Handling
The result of coroutine execution is checked so that errors can be handled and displayed.

State Management
Each route maintains its own passenger and waiting state.

XVI. LUA SYSTEM WORKFLOW
START | v Create Four Routes | v Create Coroutine for Each Route | v Start Scheduler | v Select Current Route | v Check Passenger Count | +---- Passengers < 5 ----> BOARD | +---- Passengers >= 5 ---> WAIT | v Resume Route Coroutine | v Update Route State | v Check Departure Conditions | +---- Passengers >= 8 ----> DEPART | +---- Waiting > 3 AND | Passengers >= 5 ----> DEPART | v Move to Next Route | v Continue Until 40 Cycles | v Display Final Route States | v END

XVII. LUA PROJECT FILES
Lua-Matatu-Terminus-Scheduler/ ├── main.lua └── README.md

The main source code is contained in main.lua.

XVIII. EXECUTION
The Lua project can be executed using a Lua environment or an online Lua compiler.