# Hands-on assignment 2

The subject of this assigment is creating reports. I'll create playbooks to generate a summary report of software version running on routers in the lab.

There are two versions of the playbook:
1) using regular Ansible modules (ios_facts etc.)
2) using NAPALM

Both playbooks generate the same CSV file, but NAPALM-based version appears to be much cleaner and compact.

```
hostname,sw_version
csr13,16.04.01
csr14,16.04.01
csr15,16.04.01
xrv7,5.3.0[Default]
```





