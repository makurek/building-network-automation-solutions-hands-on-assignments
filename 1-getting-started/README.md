### Hands-on assignment 1 

In this assignment I describe the lab topology I'll be using for the course. 

Also, I'll demonstrate a very basic Ansible playbook that will execute show commands on devices in the lab.

I'm using the following devices in my lab
* XRv (IOS-XR)
* CSR1000v (IOS-XE)
* vMX (Junos)
* IOS

as these are functional equivalents of devices that I use in production network.

# Lab topology

Below network represent simple Service Provider network with four CEs (R16-19) attached to PEs (vMX1, vMX3, XRv7, XRv9).
All devices are connected to a VM running Ansible via dedicated OOB interface. 

The diagram doesn't show the OOB network for the sake of simplicity.


                                         +---------------+
                                         |               |
                                         | Ansible host  |
                                         |               |
                                         |all devices are|
                                         |attached to the|
                                         |host via OOB   |
                                         |network        |
                                         +---------------+


+-----+                +-----+                +-----+                   +-----+                +-----+
|     |                |     |                |     |                   |     |                |     |
| R16 +----------------+ vMX1+----------------+ vMX2+-------------------+ vMX3+----------------+ R19 |
|     |                |     |                |     |                   |     |                |     |
+-----+                +--+--+                +--+--+                   +--+--+                +-----+
                          |                      |                         |
                          |                      |                         |
                          |                      |                         |
                          |                      |                         |
                          |                      |                         |
                          |                      |                         |
                          |                      |                         |
                          |                      |                         |
+-----+                +--+--+                +--+--+                   +--+--+                +-----+
|     |                |     |                |     |                   |     |                |     |
| R17 +----------------+XRv7 +----------------+XRv8 +-------------------+XRv9 +----------------+ R18 |
|     |                |     |                |     |                   |     |                |     |
+-----+                +--+--+                +--+--+                   +--+--+                +-----+
                          |                      |                         |
                          |                      |                         |
                          |                      |                         |
                          |                      |                         |
                          |                      |                         |
                          |                      |                         |
                       +--+--+                +--+--+                   +--+--+
                       |     |                |     |                   |     |
                       |CSR15+----------------+CSR14+-------------------+CSR13|
                       |     |                |     |                   |     |
                       +-----+                +-----+                   +-----+
