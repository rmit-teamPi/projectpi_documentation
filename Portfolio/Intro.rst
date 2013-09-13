Introduction
============

Document Intent
---------------
This design document serves as a reference, outlining all information pertaining to the 
Punnet of Berries project. It is intended to provide an overview of design considerations 
and technical specifications regarding the final implementation. Descriptions of system 
design will be shown to allow for the understanding of what is to be constructed and how 
it will be built. This document should not be considered an installation or configuration 
guide; its primary goal is to detail the design, development, and functionality of the 
cluster.

Document Overview
-----------------
Outlined in this document is the framework on which the Punnet and its accompanying 
software were developed. Each iteration in the development process is illustrated in 
detail in each section, covering system design, architecture, and implementation. Within 
this are accompanying graphical documentation and requirement specifications to aid in the 
understanding of system architecture.

Scope
-----
The breadth of the Punnet of Berries project has been intentionally delimited in order to 
make it feasible in a relatively short period of time. Given the allocated time span in which 
development has been defined, it is important to delineate any milestones that need to be
achieved in the early alpha phase of design. This will be covered in :ref:`Goals and Objectives`.
This design document is focused on core architectural design and critical parts of the system. 
As the project incorporates many pre-existing systems in conjunction with custom software, a 
large focus will be attributed to the interaction of these components.


The Punnet of Berries
---------------------

A Beowulf_ cluster is a collection of (typically) inexpensive computers, networked together 
by a local area network, usually an Ethernet, and running some parallel processing software. 
This concept puts the power of supercomputing into the hands of schools and small research 
groups.

Developed to educate and inspire the next generation of programmers, the Raspberry Pi is a 
single-board, credit card sized device. It is capable of running Linux, and other 
light-weight operating systems, with its ARM processors.

.. image:: images/raspberry_pi.jpg
    :scale: 70%
    :align: center
    :alt: Pi diagram.

The Raspberry Pi is a powerful, yet, low-cost "mini-computer". The **Punnet of Berries** 
project aims to create a Raspberry Pi *Beowulf cluster*.

.. _Beowulf: http://yclept.ucdavis.edu/Beowulf/aboutbeowulf.html
