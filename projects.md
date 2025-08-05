# Scientific Models for the involved projects:
This document illustrates component-based and detailed design models for my projects for conferences and coding interviews based on SWEBOK, and formal methods. 

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

4) Software Requirements:
  * **Functional requirements:**
    1) Open an IO pipe between the simulator terminal and the peripheral devices.
    2) Write an embedded bare-metal software on the peripheral devices to communicate data in R/W capabilities.
    3) Write an embedded Linux software on the simulator terminal device to route input data to the simulation interface and communicate back data to the perpherial devices.
  * **Non-functional requirements:**
    1) Use a full-duplex compatible protocol that supports bidirectional serial communication (e.g., UART, SATA).
    2) Handle encoding of data packets in a pre-processor automata before transmission to avoid data corruption and packet loss.
    3) Handle decoding of data packets in a post-processor automata after receiving data on the other side, whether it was a terminal side or a perpherial serial device.
    4) Handle semi-conductor logic differentials (UART TTL v.s. Inverted bipolar voltage logic).
    5) Handle encryption of data packets in a pre-processor automata for security reasons.
    6) Handle decryption of data packets in a post-processor automata for security reasons.
    7) Handle failure of sending, receiving, or processing data packets on both sides of operation.
    8) Handle different Human-Interface Devices vendors.

5) Preliminary Component-based design:
   1) _Terminal Device Component_: a physical component that runs the whole simulation.
   2) _Peripheral Device Component_: a physical component that provides the hardware to control the simulation.
   3) _Data Packet Component_: a virtual component that carries the communicant piece of information that controls the simulation.
   4) _Data Filter Component_: a virtual component that provides extra tweaks and constraints to the _data packet components_ in the form of **pre-processing** or **post-processing data filters**.
   5) _Comm Interface_: an interface specialized to provide an on-wire or wireless communication link between two or more component devices.
