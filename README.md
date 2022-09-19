# Kolla_Ansible_OpenStack_Multinode
This document is a Work-In-Progress.  It will not build a functional OpenStack cluster.  It is posted here so that I may link to it from various forums where I am recruiting help from the community.

The instructions herein attempt to build an OpenStack environment (with Ceph) inside Hyper-V on a server with 64GB RAM.  Attempting an OpenStack build on physical hardware takes too long.  When something goes wrong, it is much easier to roll back to a previous VM snapshot and try again.  Once everything is up and running, then I will modify these instructions to run on physical hardware.

Where this fails is during the final deployment step:
kolla-ansible -i /usr/local/kolla_venv/multinode deploy


# Deploy == Broken!
#  https://bugs.launchpad.net/kolla-ansible/+bug/1958268
# TASK [nova-cell : Waiting for nova-compute services to register themselves] ***********************************************************************************************************************************************************
# skipping: [kolla2]
# skipping: [kolla3]
# FAILED - RETRYING: [kolla1]: Waiting for nova-compute services to register themselves (20 retries left).
# FAILED - RETRYING: [kolla1]: Waiting for nova-compute services to register themselves (19 retries left).
# FAILED - RETRYING: [kolla1]: Waiting for nova-compute services to register themselves (18 retries left).
# FAILED - RETRYING: [kolla1]: Waiting for nova-compute services to register themselves (17 retries left).
# FAILED - RETRYING: [kolla1]: Waiting for nova-compute services to register themselves (16 retries left).
# FAILED - RETRYING: [kolla1]: Waiting for nova-compute services to register themselves (15 retries left).
# FAILED - RETRYING: [kolla1]: Waiting for nova-compute services to register themselves (14 retries left).
# FAILED - RETRYING: [kolla1]: Waiting for nova-compute services to register themselves (13 retries left).
# FAILED - RETRYING: [kolla1]: Waiting for nova-compute services to register themselves (12 retries left).
# FAILED - RETRYING: [kolla1]: Waiting for nova-compute services to register themselves (11 retries left).
# FAILED - RETRYING: [kolla1]: Waiting for nova-compute services to register themselves (10 retries left).
# FAILED - RETRYING: [kolla1]: Waiting for nova-compute services to register themselves (9 retries left).
# FAILED - RETRYING: [kolla1]: Waiting for nova-compute services to register themselves (8 retries left).
# FAILED - RETRYING: [kolla1]: Waiting for nova-compute services to register themselves (7 retries left).
# FAILED - RETRYING: [kolla1]: Waiting for nova-compute services to register themselves (6 retries left).
# FAILED - RETRYING: [kolla1]: Waiting for nova-compute services to register themselves (5 retries left).
# FAILED - RETRYING: [kolla1]: Waiting for nova-compute services to register themselves (4 retries left).
# FAILED - RETRYING: [kolla1]: Waiting for nova-compute services to register themselves (3 retries left).
# FAILED - RETRYING: [kolla1]: Waiting for nova-compute services to register themselves (2 retries left).
# FAILED - RETRYING: [kolla1]: Waiting for nova-compute services to register themselves (1 retries left).
# ok: [kolla1]
# 
# TASK [nova-cell : Fail if nova-compute service failed to register] ********************************************************************************************************************************************************************
# fatal: [kolla2]: FAILED! => {"changed": false, "msg": "The Nova compute service failed to register itself on the following hosts: kolla1,kolla2,kolla3"}
# fatal: [kolla1]: FAILED! => {"changed": false, "msg": "The Nova compute service failed to register itself on the following hosts: kolla1,kolla2,kolla3"}
# fatal: [kolla3]: FAILED! => {"changed": false, "msg": "The Nova compute service failed to register itself on the following hosts: kolla1,kolla2,kolla3"}
