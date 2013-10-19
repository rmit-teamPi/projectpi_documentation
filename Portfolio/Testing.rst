Testing
=======

----------
Tests Done
----------

Cluster Performance Tests
-------------------------
In order to test the performance and functionality of the 'Punnet of Berries' 
cluster, the system will be tested using a 'HPL (High-Performance Linpack 
Benchmark)'. This benchmark provides guesstimates of how many GFLOPS (**G** iga 
**FL** oating-point **O** perations **P** er **S** econd) of processing 
performance the Punnet of Berries cluster is able to achieve.

Once the cluster itself has been benchmarked, the 'HPL' will then be run
on a single Raspberry Pi as well as seperate system containing a modern x86/x64
based processor. This will provide a meaningful comparison with regards
to the performance gain a cluster of six Raspberry Pi's has over various other
systems.

Batch System Tests
------------------

To prove that the Berry Batch is functioning correctly, it will undergo a range of tests. 
These include, but are not limited to, the following:

+---------------------------------------+----------------------------------------+
| Test Cases                            | Expected Result                        |
+=======================================+========================================+
| Initialize the 'Punnet Scheduler'     | A total of 5 worker nodes should       |
| application with a total of 6 nodes   | report for duty.                       |
| in the cluster.                       |                                        |
+---------------------------------------+----------------------------------------+
| Initialize the 'Punnet Scheduler'     | An alert should appear advising that   |
| application with a total of 6 nodes   | two nodes have gone offline. The       |
| in the cluster. Proceed to disconnect | cluster should proceed to function     |
| two nodes.                            | as per normal.                         |
+---------------------------------------+----------------------------------------+
| Initialize the 'Punnet Scheduler'     | The application should report that 2   |
| application with 2 nodes overclocked  | priority processing nodes are available|
| to 900MHz.                            | if required.                           |
+---------------------------------------+----------------------------------------+
| View the worker nodes state table.    | Details the instantaneous system       | 
|                                       | resources of the worker nodes          |
|                                       | including processor and memory         |
|                                       | utilization for each.                  |
+---------------------------------------+----------------------------------------+
| Submit a collection of short jobs     | After running the test 10 times, some  | 
| using the "Round Robin" algorithm.    | of the job assignments to each of the  |
| (Repeat: 10 times)                    | nodes should be the same in each test. |
+---------------------------------------+----------------------------------------+
| Submit a collection of assorted jobs  | After running the test 10 times, some  |
| using the "Round Robin" algorithm.    | of the job assignments to each of the  |
| (Repeat: 10 times)                    | nodes should be different in each test.|
+---------------------------------------+----------------------------------------+
| Submit a collection of short jobs     | After running the test 10 times, the   |
| using the "First Come First Serve"    | jobs should be processed in the order  |
| algorithm.                            | the appear in the queue. This should be|
| (Repeat: 10 times)                    | consistent for each test.              |
+---------------------------------------+----------------------------------------+
| Submit a collection of assorted jobs  | After running the test 10 times, the   |
| using the "First Come First Serve"    | jobs should be processed in the order  |
| algorithm.                            | the appear in the queue. This should be|
| (Repeat: 10 times)                    | consistent for each test.              |
+---------------------------------------+----------------------------------------+
| Overclock one node to 900MHz. Submit  | The node overclocked running at 900MHz |
| a collection of jobs, including one   | should be assigned the high priority   |
| high priority job using the "Priority | job in every test which is run.        |
| Scheduling" algorithm.                |                                        |
| (Repeat: 10 times)                    |                                        |
+---------------------------------------+----------------------------------------+
| Assign one node as a priority         | The node assigned as a priority        |
| processor. Submit a collection of     | processor should be assigned the high  |
| jobs including one high priority job  | priority job in every test which is    |
| using the "Priority Scheduling"       | run.                                   |
| algorithm.                            |                                        |
| (Repeart: 10 times)                   |                                        |
+---------------------------------------+----------------------------------------+
| User views all current jobs.          | List of jobs currently in the system.  |
+---------------------------------------+----------------------------------------+
| User views a specific job.            | Details of the given job.              |
+---------------------------------------+----------------------------------------+
| User cancels a queued job.            | Confirmation of job cancellation.      |
+---------------------------------------+----------------------------------------+
| User cancels a running job.           | Confirmation of job cancellation.      |
+---------------------------------------+----------------------------------------+
| User cancels a completed job.         | Warning of invalid state.              |
+---------------------------------------+----------------------------------------+
| User cancels an already cancelled job.| Warning of invalid state.              |
+---------------------------------------+----------------------------------------+
