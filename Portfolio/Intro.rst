Introduction
============
The aim of the **Punnet of Berries** project was to create a financially viable Beowulf 
cluster, evaluate the power of the Raspberry Pi and demonstrate scheduling concepts.

This document outlines the frameowrk on which the **Punnet of Berries** and its accompanying 
software were developed. System design, architecture and implementation are all covered in 
the subsequent sections.

The Punnet of Berries
---------------------
A Beowulf_ cluster is a supercomputer built out of a collection of (typically) inexpensive 
computers. The computers are networked together by a local area network, usually Ethernet, 
and run a parallel processing software. The individual computers become the nodes of the 
supercomputer, which are combined together to form a single system. This concept puts the 
power of supercomputing into the hands of small research groups and schools. It gives them the 
ability to access the computational power that normally only large corporations can afford.

The Raspberry Pi is a single-board, credit card sized device. It is capable of running Linux, 
and other light-weight operating systems, with its ARM processors.

.. image:: images/raspberry_pi.jpg
    :scale: 70%
    :align: center
    :alt: Pi diagram.

The Raspberry Pi is a powerful, yet, low-cost "mini-computer". It was developed to educate and
inspire the next generation of programmers. **TeamPi** believes that this makes the Raspberry 
Pi an ideal candiate to create a Beowulf cluster.

The **Punnet of Berries** is a *Raspberry Pi Beowulf cluster*.

.. _Beowulf: http://yclept.ucdavis.edu/Beowulf/aboutbeowulf.html

The Berry Batch
---------------
In order for a compute cluster to function properly and fairly, its resources must be managed 
and monitored by a batch system scheduler. Batch systems enforce limits on the number of jobs 
running at one time and the resources available to them. Compute cluster users request 
resources by submitting jobs to the batch system, which then determines the scheduling that 
best utilises the resources available.

The **Berry Batch** is a custom batch system, which manages the Punnet of Berrries compute 
cluster.

As one of the aims of the Punnet of Berries is to demonstrate scheduling concepts, the Berry 
Batch implements several scheduling algorithms. The user is able to select which algorithm to
use when the cluster is initialised.
