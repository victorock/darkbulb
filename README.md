# Ansible Darkbulb

The Ansible Darkbulb project is an effort to provide a toolkit for effectively communicating and teaching Ansible topics to Network folks.

Darkbulb idea is to have materials, examples and contents that are more focused on network scenarios, expanding what is already being done by Lightbulb.

That being said, IT DOES NOT REPLACE Lightbulb.

**NOTE:** This effort is currently a work in progress and i'll try to merge in lightbulb in the future.

### What's Provided

The Ansible Darkbulb project has been designed to be used as a toolkit focused on Network to introduce Ansible thru self-paced learning thru hands-on workshops. Here you will find:

* Examples
* Topologies
* Provisioner
  * Google Computing Engine
  * Azure (Future)

#### Examples

The content in `examples/` are complete Ansible playbooks that demonstrate the most fundamental features and most common use patterns relate to network.

These examples are an excellent educational reference for communicating how Ansible works in a clear, focused and consistent manner using recommended best practices.

This content is a great source for canned demos or something you can walk-thru to illustrate automating with Ansible to a group. Some of the examples  serve as the solutions to the workshops.

#### Provisioner

It will provision everything that you need to run your personal lab environment in public clouds.

Howto (GCE):

* Setup your cloud account.
* Copy GCE service account generated file to keychain folder.
* Register your ssh public key in GCE associated as "instructor" user.
* Add your ssh-keys to your local keychain (ssh-add <file>).
* Create image with nested virtualisation.
* Edit the configuration file: group_vars/all/darkbulb.yml
* Play ansible-playbook deploy_gce_darkbulb.yml

### Requirements

* Modern HTML5 Standard Compliant Web Browser.
* A recent stable version of Python 2.7.
* The latest stable versions of Ansible.
* A SSH client such as PuTTY or Mac OSX Terminal.
* local Vagrant setup and Virtualbox.
* local ansible.

#### Assumed Knowledge

For hands-on or self-paced training, students should have working knowledge of using SSH and command line shell (BASH). The ability to SSH from their personal laptop to a lab environment hosted in a public cloud can also be required based on the format and presentation of the context.

For demos and instrcutor-led exercises, conceptual understanding of linux system admin, DevOps and distributed application architecture is all that is required.

### Reference

* [Ansible Documentation](http://docs.ansible.com)
* [Ansible Best Practices: The Essentials](https://www.ansible.com/blog/ansible-best-practices-essentials)

### License

Red Hat, the Shadowman logo, Ansible, and Ansible Tower are trademarks or registered trademarks of Red Hat, Inc. or its subsidiaries in the United States and other countries.

All other parts of Ansible Lightbulb are made available under the terms of the [MIT License](LICENSE).
