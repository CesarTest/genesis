# Genesis Node Project - Bifrost Ironic Wrapper

## 📦Installation & Setup

### Supported Platforms
* **Local Machine**: Windows 11 (via WSL) or Linux (Ubuntu/Debian).
* **Target Hypervisor**: Proxmox VE (Root privileges required).
* **Genesis Virtual Machine**: Ubuntu 24.04 Noble LTS (Fresh Installation).
* **Undercloud Engines**: OpenStack > 2026.1+ for registry-based image deployments.

---

## 🛠️ Step-by-Step Deployment Guide

### Step 1: Clone the Repository Globally
Depending on your local workstation operating system:

* **Windows 11**: Run the included automated PowerShell script. It builds a Debian WSL environment and automatically clones the repository.
  * ⚠️ *Important*: Remember to type `exit` when the foreground Debian installation finishes so the script can execute its remaining steps.
* **Linux**: Clone the repository directly into your environment:
  ```bash
  git clone https://github.com/CesarTest/genesis.git
  ```

### Step 2: Deploy the Proxmox Airgap Environment
Navigate to the root project directory on your local machine and execute the environment configuration tool:
```bash
cd genesis
./genesisCli
```
* Select **Option 10: EMULATION MENU**
* Choose **Option 2: PROXMOX**

### Step 3: Provision the Genesis VM on Proxmox
1. Download the **Ubuntu 24.04 Live Server ISO** (or find it preloaded on your attached USB drive): [Ubuntu 24.04.5 Live Server](https://releases.ubuntu.com/noble/ubuntu-24.04.5-live-server-amd64.iso)
2. Upload the ISO file into your Proxmox storage architecture.
3. Mount the ISO to the virtual CDROM drive of your newly created **Genesis Virtual Machine**.
4. Boot the Virtual Machine and initialize the Ubuntu Server installer framework.
5. Proceed through the guided OS installation using the default options. 
6. ⚠️ *Crucial*: Ensure you check the box to **install the OpenSSH Server** daemon before finishing.

### Step 4: Clone the Project inside the Genesis VM
Access your fresh Genesis VM instance via SSH or console and pull the codebase:
```bash
git clone https://github.com/CesarTest/genesis.git
```

### Step 5: Execute the Genesis Pipeline
Enter the cloned project directory within the VM and start the lifecycle execution menu:
```bash
cd genesis
./genesisCli
```
* Select **Option 8: CERTIFICATION**
* Choose **Option 2: TEST DEPLOY**

When prompted during the installation configuration, you **must explicitly toggle** the following parameters:
```text
..................Full Genesis Refresh: Yes
..Full Baremetal Virtual Nodes Refresh: Yes
.............Run Ansible in Background: Yes
```

---

## ⚙️ Configuration & Architecture

### Environment Tailoring
All custom parameterization takes place inside the `hosts/` subdirectory:
* `hosts/{environment}`: Defines specific **Hardware & Software Profiles** for your physical/virtual cluster. Use the predefined templates located in `hosts/test` as reference deployment models.
* `hosts/target`: Contains high-level **Genesis Node Customizations**, where you can manage supported operating systems, layout strategies, and target installation interfaces.

| Feature Strategy | Supported Formats / Methods |
| :--- | :--- |
| **Image Types** | `os installer` (ISO) <br> `cloud installer` (Partition: qcow/img \| Wholedisk: raw) |
| **Manifest Formats** | `cloud-init`, `kickstart`, `ignition` (Dependent on chosen OS engine) |
| **Provisioning Delivery** | `baked-in`, `config-drive`, `tftp-http` |

---

## 💡 Operational Use Cases

### 1. Hardware Lifecycle Certification
Before adding nodes into automated undercloud pipelines, the platform validates structural readiness:
* **Stage Validation**: Checks that all discrete lifecycle processes can be handled natively by OpenStack Ironic.
* **Blueprint Generation**: Output stable configuration layouts customized per Baremetal Node topology based on live telemetry test logs.

### 2. Deployment Scenarios
* **Connected Mode**: Downloads required upstream OpenStack elements and Linux images automatically to store them locally.
* **Airgap Mode**: Packages the Genesis workspace into an isolated tarball repository matrix. *(Note: Active evaluations use systems like Hauler or Zarf. RHEL/CentOS formats are preferred over Ubuntu for simplified airgap ISO mirror generation).*

---

## 🤝 Contributing & Support

### Author
* **Cesar Delgado**

### License
This ecosystem is distributed open-source under the **GPL-3.0 License**. See the `LICENSE` file for strict provisioning rights.
