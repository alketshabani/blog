---
title: "Network"
date: 2022-10-23T08:06:25+06:00
description: Network Setup in ESXi

tags: ["Homelab","Network","SIEM"]
categories: ["Basic"]
---

### ESXi Network

`I do not have a router at this point so everything will be done on my Dell PC and ESXi`

Below image shows what port groups i have created for the HomeLab machines
- Since based on the [architecture](../architecture) we will have 3 Vlans is neccessary to create 3 port groups in ESXi for our vlans.
- Also we need a trunk port group that will have all Vlans.
- Trunk and Wan will be assigned to pfsense VM

![HomeLab Architecture](/posts/HomeLab/images/esxi-network.PNG)

