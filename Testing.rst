-------
Testing
-------

Compute Cluster
---------------

- OpenMPI benchmarking

Batch System Tests
------------------

To prove that the Berry Batch is functioning correctly, it will undergo a range of tests. 
These include, but are not limited to, the following:

+---------------------------------------+----------------------------------------+
| Test Cases                            | Expected Result                        |
+=======================================+========================================+
| Submit 1 short job.                   | Confirmation. Job put in short queue.  |
+---------------------------------------+----------------------------------------+
| Submit 1 medium job.                  | Confirmation. Job put in medium queue. |
+---------------------------------------+----------------------------------------+
| Submit 1 long job.                    | Confirmation. Job put in long queue.   |
+---------------------------------------+----------------------------------------+
| Submit 1 special job.                 | Job set to wait for permission.        |
+---------------------------------------+----------------------------------------+
| One user submits a short job          | First job put in short queue.          |
| followed by one medium job.           | Second job put in medium queue.        |
+---------------------------------------+----------------------------------------+
| One user submit a short job.          | First user's job put in short queue.   |
| Second user submits a short job.      | Second user's job put in short queue   |
|                                       | after the first.                       |
+---------------------------------------+----------------------------------------+
| One user submit a short job.          | First user's job put in short queue.   |
| Second user submits a medium job.     | Second user's job put in medium queue. |
+---------------------------------------+----------------------------------------+
| One user submit a short job.          | First user's job put in short queue.   |
| Second user submits a medium job.     | Second user's job put in medium queue. |
| Third user submits a medium job.      | Third user's job put in long queue.    |
+---------------------------------------+----------------------------------------+
| User views all current jobs.          | List of jobs currently in the system.  |
+---------------------------------------+----------------------------------------+
| User views a particular user's jobs.  | List of user's jobs currently in the   |
|                                       | system.                                |
+---------------------------------------+----------------------------------------+
| User views a specific job.            | Details of the given job.              |
+---------------------------------------+----------------------------------------+
| First user views all current jobs.    | First user sees list of jobs currently |
| Second user views a specific jobs.    | in the system. Second user sees the    |
|                                       | details of the given job.              |
+---------------------------------------+----------------------------------------+
| User cancels a queued job.            | Confirmation of job cancellation.      |
+---------------------------------------+----------------------------------------+
| User cancels a running job.           | Confirmation of job cancellation.      |
+---------------------------------------+----------------------------------------+
| User cancels a completed job.         | Warning of invalid state.              |
+---------------------------------------+----------------------------------------+
| User cancels an already cancelled job.| Warning of invalid state.              |
+---------------------------------------+----------------------------------------+
| One user cancels another user's job.  | Permission denied.                     |
+---------------------------------------+----------------------------------------+

Cluster Performance Tests
-------------------------
In order to test the performance and functionality of the 'Punnet of Berries' 
cluster, the system will be tested using a 'HPL (High-Performance Linpack 
Benchmark)'. This benchmark provides guesstimates of how many GFLOPS
(**G**iga **FL**oating-point **O**perations **P**er **S**econd) of processing 
performance the 'Punnet of Berries' cluster is able to achieve.

Once the cluster itself has been benchmarked, the 'HPL' will then be run
on a single Raspberry Pi as well as seperate system containing a modern x86/x64
based processor. This will provide a meaningful comparison with regards
to the performance gain a cluster of six Raspberry Pi's has over various other
systems.
