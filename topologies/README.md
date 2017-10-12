Topologies
================================

This is an automated lab setup for Ansible training. It creates a standard topology adopting network devices from different vendors.

The functional environment will have:

* One Tower node from which Ansible will be executed and where Ansible Tower is installed.
* Two Spine switches with four network interfaces each one.
* Four Leaf switches with four network interfaces each one.
* Two Linux Servers with two network interfaces each one.

```
[MGMT]
TOWER:
  E0: VAGRANT-MGMT

[CORE]
SPINE01:
  E0: VAGRANT-MGMT
  E1: LEAF01-E1
  E2: LEAF02-E1
  E3: LEAF03-E1
  E4: LEAF04-E1

SPINE02:
  E0: VAGRANT-MGMT
  E1: LEAF01-E2
  E2: LEAF02-E2
  E3: LEAF03-E2
  E4: LEAF04-E2

[POD1]
LEAF01:
  E0: VAGRANT-MGMT
  E1: SPINE01-E1
  E2: SPINE02-E1
  E3: SRV01-E1
  E4: LEAF02-E4

LEAF02:
  E0: VAGRANT-MGMT
  E1: SPINE01-E2
  E2: SPINE02-E2
  E3: SRV01-E2
  E4: LEAF01-E4

SRV01:
  E0: VAGRANT-MGMT
  E1: LEAF01-E3
  E2: LEAF02-E3

[POD2]
LEAF03:
  E0: VAGRANT-MGMT
  E1: SPINE01-E3
  E2: SPINE02-E3
  E3: SRV02-E1
  E4: LEAF04-E4

LEAF04:
  E0: VAGRANT-MGMT
  E1: SPINE01-E4
  E2: SPINE02-E4
  E3: SRV02-E2
  E4: LEAF03-E4

SRV02:
  E0: VAGRANT-MGMT
  E1: LEAF03-E3
  E2: LEAF04-E3

```

## What's Provided

The topologies are created adopting Virtualbox tunnels to provide the interfaces connectivity.
The goals is to make it easier to expand to multiple notebooks or allow the "Data Centers Interconnection" (Notebook <-> Notebook).

* Ansible
* Cumulus
* Juniper

### Ansible

Ansible Tower and Servers based on Centos7.
This will spawn the servers connected to Leaf switches and Ansible server connected to Vagrant-MGMT Network

*Enter the Ansible Lab Folder*

```
cd <darkbulb>/topologies/Ansible
```

*Launch the Lab Environment*

>1 Tower and 0 Server
```
ansible-playbook build.yml -e topology=1t0s
```
>1 Tower and 1 Server
```
ansible-playbook build.yml -e topology=1t1s
```
>1 Tower and 2 Server
```
ansible-playbook build.yml -e topology=1t2s
```
>0 Tower and 0 Server
```
ansible-playbook build.yml -e topology=0t0s
```

### Cumulus

Network Devices based on Cumulus VX.
Cumulus does provides VX images in Vagrant Box public repository.

*Enter the Cumulus Lab folder:*

```
cd <darkbulb>/topologies/cumulus
```

*Launch the Lab Environment*

>0 Spines and 0 Leaf
```
ansible-playbook build.yml -e topology=0s0l
```
>1 Spines and 0 Leaf
```
ansible-playbook build.yml -e topology=1s0l
```
>1 Spines and 1 Leaf
```
ansible-playbook build.yml -e topology=1s0l
```
>2 Spines and 1 Leaf
```
ansible-playbook build.yml -e topology=2s1l
```
>2 Spines and 2 Leaf
```
ansible-playbook build.yml -e topology=2s2l
```
>2 Spines and 3 Leaf
```
ansible-playbook build.yml -e topology=2s3l
```
>2 Spines and 4 Leaf
```
ansible-playbook build.yml -e topology=2s4l
```

### Juniper
Network Devices based on Juniper vQFX10K.
Juniper does provides vQFX images in Vagrant Box public repository.

*Enter the Juniper Lab folder:*

```
cd <darkbulb>/topologies/juniper
```

*Launch the Lab Environment*

>0 Spines and 0 Leaf
```
ansible-playbook build.yml -e topology=0s0l
```
>1 Spine and 0 Leaf
```
ansible-playbook build.yml -e topology=1s0l
```
>1 Spines and 1 Leaf
```
ansible-playbook build.yml -e topology=1s0l
```
>2 Spines and 1 Leaf
```
ansible-playbook build.yml -e topology=2s1l
```
>2 Spines and 2 Leaf
```
ansible-playbook build.yml -e topology=2s2l
```
>2 Spines and 3 Leaf
```
ansible-playbook build.yml -e topology=2s3l
```
>2 Spines and 4 Leafs
```
ansible-playbook build.yml -e topology=2s4l
```

### How to blend and spawn your topology

Just chose devices like spine, leafs from different vendors and chose what you want to spawn.

**Ex:**

>2 Spines from Juniper:
```
    cd topologies/juniper
    ansible-playbook build.yml -e device=spine01
    ansible-playbook build.yml -e device=spine02
```
>1 Leaf from Cumulus:
```
    cd topologies/cumulus
    ansible-playbook build.yml -e device=leaf01
```
>1 Server from Ansible (POD1):
```
    cd topologies/ansible
    ansible-playbook build.yml -e device=server01
```
