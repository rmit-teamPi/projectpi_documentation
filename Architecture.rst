------------
Architecture
------------

System
------

Each Raspberry Pi will form a compute node in the Punnet of Berries cluster. 

The Berry Batch will consist of a manager which will monitor the system's resources 
and user jobs. Users will interact with the manager to submit job requests.

Daemons will run on each node


A Berry Batch daemon will run on each node, waiting for the 
