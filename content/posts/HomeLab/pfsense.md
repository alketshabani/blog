---
title: "pfSense Setup"
date: 2022-10-31T08:06:25+06:00
description: Sample post with multiple images, embedded video ect.
menu:
  sidebar:
    name: pfSense Setup
    identifier: pfsense
    parent: HomeLab
    weight: 10

tags: ["Homelab","Network","pfsense"]
categories: ["Basic"]
---

On this post i will cover pfSense configurations made:

- Vlan setup
- Firewall rules
- 

### VM setup

Since our homelab is built on top of ESXi also pfSense is stood up there.
I have allocated `1 vCPU and 1GB of Memory`, that should be enough for this setup. I have run pfSense on production environment and is not resource intensive.

### Initial Configuration

- Once pfSense is running we need to configure WAN and Lan interface
  - vmx0 is our WAN
  - vmx1 is our Lan 

- After this step is done we go to the LAN IP to open the web configurator.
- I would recommend to allow your local network to access your web configurator in WAN `although this is not advisable security wise`
  - Create a rule in your WAN interface - Firewall - Rules - WAN

### Creating VLANs

- Since we will have 3 VLANs we need to create them in pfSense.

1. Go to Interfaces -> VLANs and create your VLANs
2. Parent interface of all of your VLANs will be LAN interface

{{< img src="/posts/HomeLab/images/vlans.png" title="pfSense interfaces" >}}

3. Go to Interfaces -> Assignments and there you will see the new created VLANs.
4. After that the interfaces will show as below


### pfSense interfaces

{{< img src="/posts/HomeLab/images/pfsense.png" title="pfSense interfaces" >}}