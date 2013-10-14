Methodology
===========

Collaboration Tools
-------------------
The collaboration tools utilised for the development of the Punnet of Berries project
reflect the Open Source nature of the project.

Version Control:
    All code and documentation relating to the Punnet of Berries project is hosted in
    repositories on GitHub_ under the *rmit-teamPi* organisation. GitHub was chosen as it
    allows individual team members to use either Git or SVN depending on their own preferences.

Project Management:
    The project and bug-tracking was managed using Redmine_, an open source web-based project 
    management tool. The team's Redmine account was hosted on HostedRedmine_, a service that 
    hosts standard Redmine projects for free.

.. _GitHub: https://github.com/rmit-teamPi
.. _Redmine: http://www.redmine.org
.. _HostedRedmine: https://www.hostedredmine.com


Development Tools
-----------------
Given the collaborative effort of the development process, it is prudent to define the 
best practices and design principles to abide by. All protocols must adhere to a certain 
standard to promote scalability and ease of use. 

The design approach is one that highlights the employment of parallel processing,
concurrency, and synchronization. Fundamental operating system concepts will be
explored and integrated, exposing the Raspberry Pi as a viable platform for cluster
computing as well as comprehension of underlying technologies.

Design Principles:

- Scalability
    A computer cluster is, by nature, designed to be scalable. This inherent
    design characteristic must be adhered to, avoiding any sort of strict node 
    limitations.
- Usability
    As this project is largely for educational purposes, the cluster should
    be easily constructed with high cohesion. The final application interface 
    should also be readily accessible.
- Flexibility
    The software should be customizable, allowing users to specialize;
    secondary choices should be made available to enhance the application.


