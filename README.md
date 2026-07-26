# Genesis Node Project
## Goal 
- **PoC (Proof of Concept)**: adopt Telco Cloud Anuket  [standards](https://cntt.readthedocs.io/en/stable-kali/common/chapter00.html) and [tooling](https://ec.europa.eu/newsroom/repository/document/2025-9/TelcoCloudReferenceArchitecture_v7_L8XM9LekTSnxgxb9NgJkBBifw_113237.pdf) for Software Factories management.

## Supported Platforms
- Ubuntu 24.04 Noble fresh installation
- OpenStack > 2026.1... for registry based image deployments

## Installation
- 1) Clone Project
- 2) Use genesisCli menu to run steps of the Genesis Node Lifecycle
- 3) Configurations:
    + 3.1.- hosts/{environment} => Hardware & Software Profiles of your machines (becareful defining them well, in hosts/test examples of each deployment use case)
    + 3.2.- hosts/target        => Genesis Node Customizations, including the list of operating systems you want to deploy and the type of image:
     	- __Image Types:__ {iso/qcow-img/raw}.
		- __Install manifestos:__ {cloud-init/kickstart/ignition} depending on the OS installer used.	
		- __Install manifestos Provisioning:__ {backed-in/config-drive/tftp-http}.
		
## Scenarios
- **Genesis with Internet**... download OpenStack components and linux distros images and save it locally.
- **Genesis Airgap**... tarball Genesis project with local repository to deploy in isolated environments.
... Genesis Airgap not tested, eventually tools such [Hauler](https://ranchergovernment.com/blog/simplifying-the-airgap-experience-with-rancher-government-hauler) or [Zarf](https://zarf.dev/) should be included. Prefered CentOS/RHEL over Ubuntu since airgap repos easier to create from ISO.
- **Ansible Execution Environment** Compilation... layout is there for packaging Genesis into a Container in the future. Eventually integrate [Kolla-Ansible](https://docs.openstack.org/kolla-ansible/latest/reference/deployment-and-bootstrapping/bifrost.html) tooling for that.

## Genesis Node Life Cycle
![Genesis](./doc/genesis.jpg)

## Ironic and Ansible usage in Genesis Node
- **Deploy Stage Setup**: this node life cycle stage established how do you inject OS to instance, based on two interfaces:
 + __Boot Interface:__ depends on hardware particulars of the machine
 + __Deploy Interface:__ depends of the kind of image you want to deploy, since involve different installers and how do you provide the installer manifesto.

![Ironic](./doc/ironic.jpg)

## PoC (Proof of Concept) Scheme
![PoC](./doc/poc.jpg)

## Ironic Node Life Cycle: The State Machine
+ **Enroll = Setup each Node LifeCycle Stage** based on templates, trend is to rely on out-of-band BMC definitions as much as possible when new DMTF specifications allow it. Just the deploy stage has a big part in-band (the boot/deploy intefaces tat define PXE particulars).
[Node States Diagram](https://docs.openstack.org/ironic/latest/user/states.html) 
![States Machine](https://docs.openstack.org/ironic/latest/_images/states.svg)

## OpenStack Modules supported by standalone Ironic, but not used by installer yet.
- **Horizon plugin**... User Interface.
- **Keystone**... Authentication, Authorization, Accounting (next release will include TLS certificates handling).
- **Prometheus**... Stadistics (will be included into Ironic next release).
- **IPA Hardware Inspector**... to build hardware profiles through machine inspection (will be included into Ironic next release).

# Author
Cesar Delgado