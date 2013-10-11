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
        
-----------------------------------------------------------
Software: Architectural Considerations and Code Compilation
-----------------------------------------------------------

The Raspberry Pi hosts a single-core ARM processor, operating at 700MHz (with 
overclocking available). Due to this, any software developed for a Raspberry Pi should be
in languages that are high-level, architecturally dependent and need to be recompiled on the
Pi itself.

As there are several pre-configured Linux operating system images for the Raspberry Pi, it 
was decided that it was not necessary to create a custom Linux-From-Scratch image. In order
to choose an appropriate operating system, it was necessary to evaluate the compute cluster's 
basic needs. The key factors in the decision making process were:

- Performance
- Size
- Compatibility

With this in mind, each node in the Punnet of Berries runs the **Arch Linux Arm** operating 
system. Arch Linux is:

- ARM compatible.
- Light-weight

    - The entire image is ~150 MB.
    - The default installation is bare bones, with nothing extra included.
- Boots in around 10 seconds.

    - Allowing the entire cluster to *boot in under 20 seconds*.

