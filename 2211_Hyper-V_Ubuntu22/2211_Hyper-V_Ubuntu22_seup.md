(2022.11.18)

# Local Hyper-V Ubuntu22 Setup

## Environment

### Windows

- Windows11 Pro 22H2 (English)
  - Hyper-V Manager Version: 10.0.22621.1

### Ubuntu 22 downlod

- Ubuntu Server 22.04.1 LTS : https://jp.ubuntu.com/download
  - ubuntu-22.04.1-live-server-amd64.iso

---

## Hyper-V Setup

### Virtual Switch Manager

- Create Virtual Switch
  - External: "External Switch"

### New Virtual Machine

- Name: "u22"
- Security Generation: "Generation 2"
- Startup memory: "1024MB"
- Connection: "External Switch"
- Create a virtual hard disk: "u22.vhdx" 127GB
- Install an operating system from a bootable image file: "ubuntu-22.04.1-live-server-amd64.iso"

### Virtual Machine Settings

- Security: "Enable Secure Boot" OFF
- Memory: Dynamic Memory Maximum RAM "4096MB"

---

## Ubuntu Install

### Virtual Machine "Start"

- "Try or Install Ubuntu Server"

### Ubuntu Setup

- select your language : "English"
- keyboard layout: "Japanese" / "Japanse (OADG 109A)
- Choose the base for installation: "Ubuntu Server (minimized)"
- Network connections:
  - eth0 IPv4 "Manual"
    - Subnet: "192.168.0.0/24"
    - Address: "192.168.0.100"
    - Gateway: "192.168.0.1"
    - Name servers: "192.168.0.1"
- Profile setup
  - Your name: "m5w"
  - Your server's name: "u22"
  - Pick a username: "m5w"
  - Choose a password: ******

---

## Ubuntu First Setup

### login

```
u22 login: m5w
```

### check

```
$ cat /etc/os-release
---
PRETTY_NAME="Ubuntu 22.04.1 LTS"
NAME="Ubuntu"
VERSION_ID="22.04"
VERSION="22.04.1 LTS (Jammy Jellyfish)"
VERSION_CODENAME=jammy
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=jammy
```

### package update

```
$ sudo apt update
$ sudo apt upgrade
```
