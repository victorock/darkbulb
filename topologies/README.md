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
* Arista
* Cumulus
* Nexus (Future)

### Ansible

Ansible Tower and Servers based on Fedora25.

This will spawn the servers connected to Leaf switches and Ansible server connected to Vagrant-MGMT Network

* Enter the Ansible Lab Folder:
    cd <darkbulb>/topologies/Ansible
* Launch the Lab
    vagrant up --provider=virtualbox

### Arista

Network devices based on Arista vEOS.

Unfortunately, Arista doesn't provides the vEOS in Vagrant Box repository, but does provide it on his website:

* Go to http://www.arista.com/
* Login
* Click on Software Downloads (bottom left)
* Expand vEOS
* Download vEOS-lab-\*-virtualbox.box (example: vEOS-lab-4.18.1F-virtualbox.box)
* Save/Copy to <darkbulb>/arista/images
* Enter the Arista Lab Folder and Add Box to Vagrant:
    cd <darkbulb>/topologies/arista
    vagrant box add --name vEOS-lab-X.XX.XX images/vEOS-lab-X.XX.XX-virtualbox.box --provider=virtualbox
* Launch the Lab:
    vagrant up --provider=virtualbox

**NOTE: No license/contract is required, only an account**

### Cumulus

Network Devices based on Cumulus VX.

Cumulus does provides VX images in Vagrant Box repository.

* Enter the Cumulus Lab folder:
    cd <darkbulb>/topologies/cumulus
* Launch the Lab:
    vagrant up --provider=virtualbox

### How to blend

Just cherry pick spine, leafs from different vendors and chose what you want to spawn.

Ex:
* Spines from Arista:
    cd arista; vagrant up spine01 spine02 --provider=virtualbox

* Take Leafs from Cumulus:
    cd cumulus; vagrant up leaf01 leaf02 leaf03 leaf04 --provider=virtualbox
