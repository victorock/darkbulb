# Ansible Darkbulb

The Ansible Darkbulb project is an effort to provide a toolkit for effectively communicating and teaching Ansible topics to Network folks.

Darkbulb idea is to have materials, examples and contents that are more focused on network scenarios, expanding what is already being done by Lightbulb.

That being said, IT DOES NOT REPLACE Lightbulb.

**NOTE:** This effort is currently a work in progress and i'll try to merge in lightbulb in the future.

## What's Provided

The Ansible Darkbulb project has been designed to be used as a toolkit focused on Network to introduce Ansible thru self-paced learning thru hands-on workshops. Here you will find:

* Examples
* Topologies
* Provisioner
  * Google Computing Engine
  * local machine w/ Vagrant
  * Azure (Future)

## Examples

The content in `examples/` are complete Ansible playbooks that demonstrate the most fundamental features and most common use patterns relate to network.

These examples are an excellent educational reference for communicating how Ansible works in a clear, focused and consistent manner using recommended best practices.

This content is a great source for canned demos or something you can walk-thru to illustrate automating with Ansible to a group. Some of the examples  serve as the solutions to the workshops.

## Provisioner

It will provision everything that you need to run your personal lab environment in public clouds.

All provisioners require Ansible to run.  
  * [Ansible Installation](http://docs.ansible.com/ansible/latest/intro_installation.html)

### How-to GCE:

* Setup your GCE account.
  1. [Installation and Setup Directions](https://cloud.google.com/deployment-manager/docs/step-by-step-guide/installation-and-setup)
    Follow just these parts:
    * **Create a project**
    * **Enable APIs for which you want to use Deployment Manager**
  2. [Ansible Google Cloud Platform Guide](http://docs.ansible.com/ansible/latest/guide_gce.html)
    Follow just these parts:
    * **Introduction**
    * **Credentials**  
* Copy GCE service account generated file to keychain folder in darkbulb project:
  e.g. `cp ~/Downloads/MyKeyName.json darkbulb/provisionner/keychain/MyKeyName.json`
* Install PyCrypto: `pip install PyCrypto`
* Register your ssh public key in GCE associated as "instructor" user.
  * [Adding or removing project-wide public SSH keys](https://cloud.google.com/compute/docs/instances/adding-removing-ssh-keys#project-wide)
* Add your private ssh-key to your local keychain (if not already done)
  e.g. `ssh-add <filename>`
* Create image with nested virtualization.
  * [Enabling Nested Virtualization for VM Instances](https://cloud.google.com/compute/docs/instances/enable-nested-virtualization-vm-instances)
* Edit the configuration file: darkbulb/provisionner/vars/main.yml
* Run the playbook: `ansible-playbook deploy_gce_darkbulb.yml`

### How-to local machine w/ Vagrant)
Instructions coming soon

#### Requirements

* Modern HTML5 Standard Compliant Web Browser.
* A recent stable version of Python 2.7.
* The latest stable versions of Ansible.
* A SSH client such as PuTTY or Mac OSX Terminal.
* local Vagrant setup and Virtualbox.
* local Ansible.

### How-to Azure
Coming soon

## Assumed Knowledge

For hands-on or self-paced training, students should have working knowledge of using SSH and command line shell (BASH). The ability to SSH from their personal laptop to a lab environment hosted in a public cloud can also be required based on the format and presentation of the context.

For demos and instructor-led exercises, conceptual understanding of linux system admin, DevOps and distributed application architecture is all that is required.

## Reference

* [Ansible Documentation](http://docs.ansible.com)
* [Ansible Best Practices: The Essentials](https://www.ansible.com/blog/ansible-best-practices-essentials)
* [Integration: Network Automation with Ansible](https://www.ansible.com/integrations/networks)

## License

Red Hat, the Shadowman logo, Ansible, and Ansible Tower are trademarks or registered trademarks of Red Hat, Inc. or its subsidiaries in the United States and other countries.

All other parts of Ansible Lightbulb are made available under the terms of the [MIT License](LICENSE).
