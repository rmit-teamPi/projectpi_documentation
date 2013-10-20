Summary
=======
**A Punnet of Berries** is a project created by **Team Pi** which employs the use 
of a Raspberry Pi computing cluster to perform batch scheduling and processing of
jobs submitted to the 'Berry Batch' application software. This custom written
piece of software utilises a number of technologies to assign and distribute 
jobs based on predefined user selectable algorithms. These scheduling algorithms
include the *Round Robin*, *First Come First Serve* and *Priority Scheduling*
algorithms, with the software being easily expandable to incorporate a variety
of other scheduling algorithms. Using a master and slave model of communication, 
the cluster utilises the CPU processing power of each the slaves nodes to 
execute jobs and report back their results to the master node.

With the Raspberry Pi CPU clock speed coming in at a decent, but conservative,
700MHz, future implementations of the **Berry Batch** software could incorporate 
the use of the Raspberry Pi's onboard GPU to boost the raw processing power each
node and as a result the raw processing power of the entire cluster.

--------------------------------------------------------------------------------

When setting out to build a Raspberry Pi computing cluster, one should never 
aim to create a system capable of making the list of the Top 500 supercomputers 
in the world. After all, such a cluster is no substitute for a true
supercomputer.

So what's the point you ask?

While the sheer performance of a Raspberry Pi computer cluster will never come 
close to that of a modern day supercomputer, it's a fantastic and fundamental 
representation of a full scale supercomputer on a budget. Sure the performance 
per dollar ratio will never even come close to that of a true supercomputer, but 
there's one major benefit to creating an RPi cluster. It's relatively affordable 
for anyone who would like to build one. Traditionally supercomputers have been 
reserved for organisations and educational institutions who can afford them. 
This means that access to such systems is often limited and out of reach for 
most individuals.

With the birth and release of the Raspberry Pi onto the market, thousands of 
interesting projects were brought to life. With the cost of a single unit coming
in at approximately $35 (depending on country), the idea of a building a
distributed computing cluster on a budget was made a reality. With only a couple
hundred dollars spent, individuals can now have access to a mini-supercomputer
in their own home.
