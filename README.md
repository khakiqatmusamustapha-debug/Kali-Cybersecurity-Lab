# 🛡️ Virtual Cybersecurity Lab Using VirtualBox and Kali Linux

A hands-on cybersecurity lab project documenting the setup of **Kali
Linux in Oracle VirtualBox**, the creation of a private **NAT Network**,
manual IPv4 configuration, connectivity preparation, and a recovery
snapshot.

This repository records my practical learning process and provides a
reference for rebuilding the same lab. The environment is intended for
learning and **authorized security testing only**.

------------------------------------------------------------------------

## 📌 Project Overview

This project focuses on building a virtual cybersecurity and
penetration-testing laboratory using **Oracle VirtualBox** and **Kali
Linux**.

The aim is to create a controlled environment where I can learn and
practise cybersecurity concepts, network configuration, reconnaissance,
vulnerability assessment, packet analysis, and security-tool usage
without testing systems without permission.

The lab uses a VirtualBox NAT Network so that other virtual machines can
be added to the same lab network later. Screenshots in this repository
document the configuration and progress.

------------------------------------------------------------------------

## 🎯 Objectives

The main objectives of this project are to:

-   Install and configure Oracle VirtualBox.
-   Set up Kali Linux as a virtual machine.
-   Create or select a private NAT Network named `NatNetwork`.
-   Attach the Kali Linux VM to the NAT Network.
-   Configure a manual IPv4 address, gateway, and DNS server in Kali
    Linux.
-   Check network connectivity and DNS resolution.
-   Create a clean virtual-machine snapshot for recovery.
-   Document the setup with screenshots.
-   Prepare the environment for future authorized cybersecurity
    projects.

------------------------------------------------------------------------

## 🛡️ Purpose of the Lab

This lab provides an isolated, manageable environment for cybersecurity
learning and authorized testing.

It can be used for activities such as:

-   Network reconnaissance on lab systems
-   Port scanning on systems I own or have permission to test
-   Vulnerability assessment
-   Packet analysis
-   Web security testing in a local test environment
-   Safe experimentation with security tools
-   Practising Linux and network administration

> ⚠️ **Important:** Only test systems you own or have explicit
> permission to assess. Keep experiments within your authorized lab
> environment.

------------------------------------------------------------------------

## 🏗️ Lab Architecture

The current setup consists of a Windows host, Oracle VirtualBox, and a
Kali Linux virtual machine connected to a NAT Network.

``` text
                 Windows Host
                      |
               Oracle VirtualBox
                      |
              Virtual Machine: Kali
                      |
            VirtualBox NAT Network
                  NatNetwork
                      |
              Lab subnet: 10.0.0.0/24
                      |
          Future authorized lab machines
```

The network is designed so that additional test machines can be
connected to the same NAT Network in future projects.

------------------------------------------------------------------------

## ⚙️ Lab Configuration

  🧩 Component                     ⚙️ Configuration
  -------------------------------- -----------------------
  Host operating system            Windows
  Virtualization software          Oracle VirtualBox
  Security operating system        Kali Linux
  Virtual machine                  Kali
  Virtual network mode             NAT Network
  NAT Network name                 `NatNetwork`
  Network address shown in setup   `10.0.0.0/24`
  Kali IPv4 address configured     `10.0.0.2/24`
  Default gateway entered          `10.0.0.1`
  DNS server entered               `8.8.8.8`
  Recovery point                   `My Fresh Kali Linux`

*Note:* These values reflect the configuration visible in my
screenshots. Confirm the actual interface and gateway values in your own
VirtualBox setup before reusing them.

------------------------------------------------------------------------

## 🪜 Lab Setup Procedure

### Step 1. Install the Required Tools

I prepared Oracle VirtualBox on the Windows host and used a Kali Linux
virtual machine for the cybersecurity environment.

**Tools used:** - Oracle VirtualBox - Kali Linux

### Step 2. Create or Check the NAT Network

In VirtualBox's **Network / NAT Networks** manager, I checked the
private network configuration.

The network shown in the setup uses the `10.0.0.0/24` subnet, with DHCP
enabled in the NAT Network manager.

**Screenshot:**

![VirtualBox NAT Network Manager](assets/01-nat-network-manager.jpeg)

### Step 3. Attach Kali Linux to the NAT Network

I opened the Kali virtual machine's settings, selected **Network**,
enabled the network adapter, and selected **NAT Network** as the
attachment type. The selected network name was `NatNetwork`.

**Screenshot:**

![Kali VM network adapter
settings](assets/02-virtualbox-kali-network-settings.jpeg)

### Step 4. Configure the IPv4 Settings in Kali Linux

In Kali Linux, I opened the wired connection settings and selected
**IPv4 Settings**. I changed the method to **Manual** and entered the
values below.

  Setting            Value
  ------------------ ------------
  Address            `10.0.0.2`
  Netmask / prefix   `/24`
  Gateway            `10.0.0.1`
  DNS server         `8.8.8.8`

**Screenshot:**

![Kali Linux manual IPv4
configuration](assets/03-kali-static-ipv4-settings.jpeg)

### Step 5. Start Kali Linux and Check the Environment

I started the Kali Linux virtual machine and confirmed that the Kali
desktop loaded.

**Screenshot:**

![Kali Linux desktop running in
VirtualBox](assets/04-kali-linux-desktop.jpeg)

### Step 6. Create a Recovery Snapshot

After configuring the lab, I opened the VirtualBox snapshot interface
and prepared a snapshot named **`My Fresh Kali Linux`**. The description
recorded that the IP address and internet connection were working.

A snapshot provides a recovery point that can be useful before later
experiments or configuration changes.

**Screenshot:**

![VirtualBox snapshot dialog](assets/06-kali-clean-snapshot.jpeg)

------------------------------------------------------------------------

## 🧪 Verification Checklist

Use this checklist when validating the lab. Mark each item complete only
after checking it on your own machine.

-   [ ] Kali Linux starts successfully.
-   [ ] The Kali network adapter is connected to `NatNetwork`.
-   [ ] The IPv4 address and prefix are correct for the lab.
-   [ ] The configured gateway is reachable.
-   [ ] DNS resolution works.
-   [ ] Internet access works if it is intended and allowed by the NAT
    Network configuration.
-   [ ] A recovery snapshot has been saved.

Useful, non-destructive checks inside Kali include:

``` bash
ip address
ip route
cat /etc/resolv.conf
ping -c 4 10.0.0.1
getent hosts example.com
```

The gateway test will only succeed if `10.0.0.1` is the correct
reachable gateway for the configured network. If a check fails, verify
the VirtualBox NAT Network settings and the guest's network
configuration before changing values.

------------------------------------------------------------------------

## 🧠 What I Learned

### 1. Virtualization

I practised using VirtualBox to run Kali Linux in a virtual machine
instead of installing it directly on the host computer.

### 2. NAT Network Configuration

I learned how a VirtualBox NAT Network can connect virtual machines
through a private virtual subnet and how a network can be prepared for
additional lab machines.

### 3. Static IPv4 Configuration

I practised entering an IPv4 address, prefix length, gateway, and DNS
server in Kali Linux's network settings.

### 4. Snapshots and Recovery

I learned the value of saving a known-good snapshot before making
further configuration changes or conducting experiments.

### 5. Documentation

I recorded the setup using screenshots and configuration notes so the
process can be reviewed and repeated.

------------------------------------------------------------------------

## 🔐 Security & Ethical Use

This laboratory is intended for **education and authorized security
testing only**.

-   Test only systems you own or have explicit permission to assess.
-   Keep practice targets within the intended lab environment.
-   Take a snapshot before making major changes.
-   Do not scan, exploit, or interfere with public or third-party
    systems without authorization.
-   Protect credentials and avoid publishing secrets in screenshots or
    repository files.

------------------------------------------------------------------------

## 🚀 Future Improvements

Possible next steps for this project include:

-   Add a deliberately vulnerable virtual machine as an authorized
    target.
-   Document additional network and DNS troubleshooting.
-   Practise packet analysis in the lab.
-   Record controlled vulnerability-assessment exercises.
-   Add sanitized screenshots and notes for each new milestone.

------------------------------------------------------------------------

## 📂 Repository Structure

``` text
kali-cybersecurity-lab/
├── README.md
└── assets/
    ├── 01-nat-network-manager.jpeg
    ├── 02-virtualbox-kali-network-settings.jpeg
    ├── 03-kali-static-ipv4-settings.jpeg
    ├── 04-kali-linux-desktop.jpeg
    ├── 05-virtualbox-manager.jpeg
    └── 06-kali-clean-snapshot.jpeg
```

------------------------------------------------------------------------

## 👩‍💻 Project Status

**Status:** Initial lab setup documented.

This is a practical learning project. I will continue updating the
repository as I verify connectivity, improve the lab, and complete
additional authorized cybersecurity exercises.

------------------------------------------------------------------------

*Kali-Cybersecurity-Lab

My hands-on Cybersecurity Lab using VirtualBox and Kali Linux.

This laboratory is intended strictly for educational purposes only.

⸻

🔗 Tools & Resources

* VirtualBox: https://virtualbox.org/wiki/Downloads
* Kali Linux: https://kali.org/get-kali
  
⸻

👤 Author

Musa-Mustapha Khakiqat

Cybersecurity Student B084

LinkedIn:
https://www.linkedin.com/in/khakiqat-musa-mustapha-551905434

⸻

📌 Project Information

Program Name: Cybersecurity at Networkwalks
Week: 01
Project: Cybersecurity & Pentesting Lab Setup
Repository: GitHub

⸻

🎯 Project Objective

To build a practical cybersecurity laboratory using VirtualBox and Kali Linux, configure network connectivity, and prepare a controlled environment for learning cybersecurity and penetration-testing fundamentals.

⸻

🧪 Lab Environment

* Host Operating System: Windows
* Virtualization Software: Oracle VirtualBox
* Guest Operating System: Kali Linux
* Network Configuration: NAT Network and manual IPv4 configuration

⸻

⚠️ Disclaimer

All activities in this laboratory are for educational purposes and authorized testing only. Never test systems or networks without permission. as part of my hands-on cybersecurity learning journey.*
