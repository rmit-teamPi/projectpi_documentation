Design Considerations
=====================

.. _goals:

--------------------
Goals and Objectives
--------------------

The Punnet of Berries project aims to create a financially viable Beowulf cluster, which 
is energy efficient and demonstrates the advantages of parallel computing. This will be 
achieved by utilising inexpensive hardware and open source technologies. In order to 
function properly, the system's resources will need to be managed and allocated by a batch 
scheduler. The Punnet of Berries will be accompanied by a custom batch system, the 
*Berry Batch*.

**Priority Objectives**

    - Establish open source tools that will be utilized.
    - Generate system topology and determine appropriate interfaces.
    - Develop system and application design.
    - Determine most appropriate software development methodology.

**Functional Requirements**

    - The user must be able to specify the number of cores to undertake any given job.
    - The Batch master must be able to support as many slave nodes as possible.

*These requirements will be expanded on throughout development.*

**Non-functional Requirements**

    - Scalability
    - Testability
    - Reliability
    - Documentation
    - Open Source

-----------
Constraints
-----------

Hardware: Raspberry Pi
----------------------

The Raspberry Pi is a comparatively low end single-board computer. As such, the design
process must accommodate for these hardware specifications:

    - SoC (System on a Chip) Broadcom BCM2835
    - 700 MHz ARM core
    - VideoCore IV GPU
    - 512 MB of SDRAM.

Aside from an SD card, the Raspberry Pi does not feature any sort of non-volatile storage.
Efficiency is a concern when constrained to a low capacity memory card. There is also an 
interface bottleneck, as both the USB and Ethernet share the same bandwidth.

An additional concern is of power distribution in regards to scalability; this would likely 
be resolved with the utilization of custom power supplies, but nonetheless it is something 
to consider.
        
Software: Parallelism and Concurrency
-------------------------------------

An area of concern is the difficulty of developing software which executes
computations in a parallel manner, by distributing them across multiple cores. 

Software: Architectural Considerations and Code Compilation
-----------------------------------------------------------

The Raspberry Pi hosts a single-core ARM processor, operating at 700MHz (with 
overclocking available). Due to this, any software developed will be in languages that 
are high-level, architecturally dependent and need to be recompiled on the Pi itself.

-----------
Methodology
-----------

Collaboration Tools
-------------------

The collaboration tools utilised for the development of the Punnet of Berries project
reflect the Open Source nature of the project.

**Version Control**
All code and documentation relating to the Punnet of Berries project will be hosted in
repositories on GitHub_ under the *rmit-teamPi* organisation.

.. _GitHub: https://github.com/rmit-teamPi

**Project Management**
The project and bug-tracking will be managed using Redmine, an open source web-based project 
management tool. The Redmine account will be hoseted for free on HostedRedmine_.

.. _HostedRedmine: https://www.hostedredmine.com


Development
-----------

Given the collaborative effort of the development process, it is prudent to define the 
best practices and design principles to abide by. All protocols must adhere to a certain 
standard to promote scalability and ease of use. 

The design approach is one that highlights the employment of parallel processing,
concurrency, and synchronization. Fundamental operating system concepts will be
explored and integrated, exposing the Raspberry Pi as a viable platform for cluster
computing as well as comprehension of underlying technologies.

Design Principles:

- Scalability
    A computer cluster is, by nature, designed to be scalable. This inherent
    design characteristic must be adhered to, avoiding any sort of strict node 
    limitations.
- Usability
    As this project is largely for educational purposes, the cluster should
    be easily constructed with high cohesion. The final application interface 
    should also be readily accessible.
- Flexibility
    The software should be customizable, allowing users to specialize;
    secondary choices should be made available to enhance the application.


