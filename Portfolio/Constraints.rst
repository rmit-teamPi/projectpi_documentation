Constraints
===========

----------------------
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
        
-------------------------------------
Software: Parallelism and Concurrency
-------------------------------------

An area of concern is the difficulty of developing software which executes
computations in a parallel manner, by distributing them across multiple cores. 

-----------------------------------------------------------
Software: Architectural Considerations and Code Compilation
-----------------------------------------------------------

The Raspberry Pi hosts a single-core ARM processor, operating at 700MHz (with 
overclocking available). Due to this, any software developed will be in languages that 
are high-level, architecturally dependent and need to be recompiled on the Pi itself.
