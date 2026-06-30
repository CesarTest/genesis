# Genesis Node Project
## Goal 
- **PoC (Proof of Concept)**: adopt Telco Cloud Anuket  [standards](https://cntt.readthedocs.io/en/stable-kali/common/chapter00.html) and [tooling](https://ec.europa.eu/newsroom/repository/document/2025-9/TelcoCloudReferenceArchitecture_v7_L8XM9LekTSnxgxb9NgJkBBifw_113237.pdf) for Software Factories management.

## Supported Platforms
- Ubuntu 24.04 Noble fresh installation... under development.

## Installation
- 1) Clone Project
- 2) Use genesisCli menu to run steps of the Genesis Node Lifecycle 

## Scenarios
- **Genesis with Internet**... download OpenStack components and linux distros images and save it locally.
- **Genesis Airgap**... tarball Genesis project with local repository to deploy in isolated environments.
... Genesis Airgap not tested, eventually tools such [Hauler](https://ranchergovernment.com/blog/simplifying-the-airgap-experience-with-rancher-government-hauler) should be included. Prefered CentOS/RHEL over Ubuntu since airgap repos easier to create from ISO.
- **Ansible Execution Environment** Compilation... layout is there for packaging Genesis into a Container in the future. 
... Actually, Genesis should run in a dedicated machine instead of container.

## Genesis Node Life Cycle
![Genesis](./doc/genesis.jpg)

## Ironic and Ansible usage in Genesis Node
![Ironic](./doc/ironic.jpg)

## PoC (Proof of Concept) Scheme
![PoC](./doc/poc.jpg)

## OpenStack Modules supported by standalone Ironic, but not used by installer yet.
- **Horizon plugin**... User Interface.
- **Keystone**... Authentication, Authorization, Accounting.
- **Prometheus**... Stadistics.
- **IPA Hardware Inspector**... to build hardware profiles through machine inspection.

# Author
Cesar Delgado