# Hands-on assignment 2

In this assignment I'll create playbooks that generate a summary report of SW version running on lab routers.

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

Both playbooks are based on the same theme:

1. Perform initial cleanup, removing existing directories and files
2. Create temporaty and output directories 
3. Collect interesting data
  a) either using ios_facts and iosxr_facts
  b) or using napalm_get_facts
4. Use jinja2 templates to generate CSV files
5. Assemble intermediate files into a report file










