# [-THE MODULE/FRAMEWORK IS NOT RELEASED YET-]

# EASYXEN - Introduction

Easyxen is a custom Ansible Module to automatically manage VM on XEN server hypervisors.

The module include the following feature:

- [x] Create/remove VM.
- [ ] Reconfigure VM.
- [x] Start/stop VM.
- [ ] Build templates in automation.
- [ ] Put userdata during the VM creation. (like AWS)
- [ ] Running Ansible playbook after VM creation
- [ ] VM hardening via Ansible roles integrated (after the VM is created).
- [ ] Hypervisor health and usage reports
- [X] Reproduce all your private cloud infra automatically

*THIS SOFTWARE IS NOT RELEASED YET. SO, SOME OF THESE FEATURES ARE NOT
 AVAILABLE RIGHT NOW, BUT THEY WILL BE SOON.

# Requirements
packages_required: sshpass

Supported distro: Centos, Debian, Redhat, Ubuntu
....Soon Available ...


# Usage Guide

....Soon Available ...

#Base Images management

....Soon Available ...

# Software Architecture and Idea  [DRAFT/IN_PROGRESS]

The idea is to make a completely modular software which will work as a little framework to manage XEN with Bash and/or Python.

So, all the reusable code and functions wil be put in the '/lib/basic.sh', that will work as a container where the other modules and functions will take the 'global' functions.

Indeed, this file contain functions that are used across the various states of the VMs. It is containing functions like:

- Is the virtual machine present?
- Is the exit code ok?
- Log for me this message.
- Is VM deleted?
- Give me the UUID of the virtual machine.
... And Other

The file is written and will be extended in BASH. 
Is automatically laoded in the first phase of the runtime process by the Ansible module entrypoint which is "/easyxen".

This approach allow us to share functions that repeat every time.

As the best practies for Ansible modules every VM have a 'state' which represent how you want your VM (halted, run, absent/removed ...).
Every state work with the 'desidered state' concept, so it will not do any operations if the situation is already as we want.

===========================================================================


TEMP_TODO_NOTE:

- base_image -> Automated CIS benchmark.
- docs -> Create guideline and script to build base images.
- @all -> Test remote execution and caching system.
- @all -> Create script to check syntax and lint of the module like pylint.
- @all -> Output for ansible
- @all -> Add common Lint and syntax check for BASH.
- [WIP] prenset.sh -> Add userdata option.
- present.sh -> Add DHCP option.
- present.sh -> Create configuration per distro.
- present.sh -> custom DNS (optional).
- present.sh -> Image download and cache on the XEN system
- present.sh -> Handle multiple vif (hardware & OS configuration).
- present.sh -> Add Task Contributor
- absent.sh -> Add keep disks feature.
- [WIP] reconfigure.sh -> Handle disks better