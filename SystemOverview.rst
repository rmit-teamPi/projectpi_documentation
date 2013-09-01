System Overview
===============

In order for a compute cluster to function properly and fairly, its resources must 
be managed and monitored by a batch system scheduler. Batch systems enforce 
limits on the number of jobs running at one time and the resources available to them. 
Compute cluster users request resources by submitting jobs to the batch system, which
then determines the scheduling that best utilises the resources available.

The Punnet of Berries compute cluster will be managed by a custom batch system, the 
*Berry Batch*.

--------------------
Goals and Objectives
--------------------

--------
Topology
--------

A chain is only as strong as its weakest link and in a distributed model super
computer, this statement cannot be any more accurate. No matter how quickly each
individual node can process the tasks which it is given, if the communications
link between the master system and each of the slave nodes becomes a bottleneck,
then the entire system will suffer in performance.

In order to produce an efficient, flexible and redundant system, the selection of 
a networking topology which can fulfil those three specific characteristics is
crucial. By selecting the star network topology as the basis for the 'Punnet of 
Berries' super computer, the key requirements of efficiency, flexibility and 
redundancy are met.

Efficiency
----------
By design, star networks utilise a central hub such as a networking switch to
handle to flow of packets in a network. This allows data packets to only travel
to those nodes which they are intended for, reducing the overall traffic in the
network.

Flexibility
-----------
By utilising a central hub for communications, a star network can easily be
expanded to support additional nodes without affecting the entire network.
Furthermore nodes can be removed at any time, if servicing is required.

Redundancy
----------
By utilising a central hub for communications, the likelihood of total system
failure is greatly reduced. Whilst failure of the central hub would mean that
the entire system is brought down, failure of an individual node wouldn't have
any affect on the overall system.
