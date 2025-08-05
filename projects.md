# Scientific Models for the involved projects:
This document illustrates component-based and detailed design models for my projects for conferences and coding interviews. 

## The following contents are to be described:
* Problem synthesis and definition.
* Problem decomposition.
* Problems grouping.
* Problem-problem relationship.
* Solution derivation.
* Solution decomposition.
* Problems-Solutions mapping.
* Component-based model.
* Components relations derivation (i.e., component interfaces).
* Detailed and constructional design.
* Technology Stack and target projects.

## Serial4j Model:
1) Problem synthesis and definition: controlling graphics and physics simulation via an external hardware, or interfacing existing hardware with a simulation software.
2) Problem decomposition: We could subdivide this larger problem into much smaller subsets of problems, in the essence to start deriving simple solutions. Controlling software simulation has various aspects that need to be demystified; **first and foremost** the hardware-software communication protocol compatibility aspect; **second to that** is the hardware design and software design problems. 

> [!NOTE]
> ## Hardware design problems (both functional and non-functional) including:
> 1) MCU characteristics and power.
> 2) MCU firmware (protocol selection, setup, and closure) and flashing ROMs.
> 3) Bootloader control.
> 4) Memory management.
> 5) Fault tolerance management and error check.
>
> ## Software design problems (both functional and non-functional) including:
> 1) Establishing connection.
> 2) Data framing and buffering routines.
> 3) Anti-failure handlers.
> 4) Closing connection.
>

3) Problem-problem relationship: There are relations among problem components; both uni-directional and bi-directional relations can exist so far. For example, a relation among MCU firmware, communication protocol, and software design could be derivated.

4)
