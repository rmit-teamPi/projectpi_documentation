System Overview
===============

In order for a compute cluster to function properly and fairly, its resources must 
be managed and monitored by a batch system scheduler. Batch systems enforce 
limits on the number of jobs running at one time and the resources available to them. 
Compute cluster users request resources by submitting jobs to the batch system, which
then determines the scheduling that best utilises the resources available.

The Punnet of Berries compute cluster will be managed by a custom batch system, the 
*Berry Batch*.

--------------
Specifications
--------------

Hardware
--------
+-----------------+-----+------------------------------------+--------------+-----------+------------+
| Category        | Qty | Description                        | Supplier     | Unit Cost | Total Cost |
+=================+=====+====================================+==============+===========+============+
| Computer        |   6 | Raspberry Pi Model B 512MB         | element14    |    $41.80 |    $250.80 |
+-----------------+-----+------------------------------------+--------------+-----------+------------+
| Storage         |   6 | Assorted brands 8GB SD card        | MULTIPLE     |    $12.00 |     $72.00 |  
+-----------------+-----+------------------------------------+--------------+-----------+------------+
| Enclosure/Case  |   6 | Raspberry Pi Case (Clear)          | element14    |     $9.79 |     $58.74 |
+-----------------+-----+------------------------------------+--------------+-----------+------------+
| Power Supply    |   6 | Power Supply USB 5V/1.2A           | element14    |    $22.00 |    $132.00 |
+-----------------+-----+------------------------------------+--------------+-----------+------------+
| Ethernet Cables |   6 | 1.5m Cat-5e Patch Cable            | MULTIPLE     |     $3.00 |     $18.00 |
+-----------------+-----+------------------------------------+--------------+-----------+------------+
| Switch          |   1 | 8-Port 10/100 Mbps Ethernet Switch | UNKNOWN      |    $34.00 |     $34.00 |
+-----------------+-----+------------------------------------+--------------+-----------+------------+

Software
--------
The operating system of choice for the Punnet of Berries super computer is a
ported version of Arch Linux for ARM processors. This linux variant is very
lightweight and only requires approximately 130MB of disk space, packing in only
the bare essentials required for a functional operating system.

In addition to the operating system, the following applications will be installed:

- GCC
- Open MPI
- Python 2
- Python 3
