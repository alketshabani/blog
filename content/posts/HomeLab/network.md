---
title: "Network"
date: 2022-10-23T08:06:25+06:00
description: Network Setup in ESXi
menu:
  sidebar:
    name: Network 
    identifier: Network
    parent: setup
    weight: 10

tags: ["Homelab","Network","SIEM"]
categories: ["Basic"]
---

### ESXi Network

Below image shows what port groups i have created for the HomeLab machines
- Since based on the [architecture](/content/posts/HomeLab/architecture.md) we will have 3 Vlans is neccessary to create 3 port groups in ESXi for our vlans.
- Also we need a trunk port group that will have all Vlans.
- Trunk and Wan will be assigned to pfsense VM

{{< img src="/posts/HomeLab/images/esxi-network.jpg" title="HomeLab Architecture" >}}