# Genesis Node Project
## Goal 
- **PoC (Proof of Concept)**: adopt Telco Cloud Anuket  [standards](https://cntt.readthedocs.io/en/stable-kali/common/chapter00.html) and [tooling](https://ec.europa.eu/newsroom/repository/document/2025-9/TelcoCloudReferenceArchitecture_v7_L8XM9LekTSnxgxb9NgJkBBifw_113237.pdf) for Software Factories management.

## Supported Platforms
- Ubuntu 24.04 Noble fresh installation... under development.

## Installation
- 1) Clone Project
- 2) Follow genesisCli menu guidelines

## Scenarios
- **Genesis with Internet**... download OpenStack components and linux distros images and save it locally.
- **Genesis Airgap**... tarball Genesis project with local repository to deploy in isolated environments.
... Genesis Airgap not tested, eventually tools such [Hauler](https://ranchergovernment.com/blog/simplifying-the-airgap-experience-with-rancher-government-hauler) should be included. 
- **Ansible Execution Environment** Compilation... layout is there for packaging Genesis into a Container in the future. 
... Actually, Genesis should run in a dedicated machine instead of container.

## PoC (Proof of Concept) Scheme
![PoC](./doc/pco.jpg)

## Ironic and Ansible usage in Genesis Node
![Ironic](./doc/ironic.jpg)

## Genesis Node Life Cycle
![Genesis](./doc/genesis.jpg)

# Author
Cesar Delgado