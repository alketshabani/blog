---
title: "Walkthrough - SOC164 - Suspicious Mshta Behavior"
date: 2022-12-29T08:06:25+06:00
description: Architecture overview of the HomeLab

tags: ["LetsDefend","BlueTeam","Suspicious Mshta Behavior"]
categories: ["SOC"]
---


## What is LetsDefend


> For those who are not familiar [LetsDefend](https://app.letsdefend.io/) is a site mainly focused for BlueTeam professionals and especially SOC members. 
![](/posts/LetsDefend/images/20221229193220.png)  


## EventID 114


![](/posts/LetsDefend/images/20221229194235.png)  


> From the alert we see that it is related with [LolBins](https://lolbas-project.github.io/). LolBins or *Living of the land binaries* are binaries of a non-malicious nature, local to the operating system, that have been utilised and exploited by cyber criminals and crime groups to camouflage their malicious activity.


## Investigation

>Once we have assigned the alert to ourselves we create an investigation for our alert.

![](/posts/LetsDefend/images/20221229195548.png)  

>starting the playbook will walk us through the validation of the alert

## 1. Identify the Binary

![](/posts/LetsDefend/images/20221229200143.png)  

> In order to find the binary we can use the monitoring tab, and you can see in the Event image it is noted what the binary was. Also if you go to Endpoint Security and search for `Roberto` machine and afterwards go to command history you will see:

![](/posts/LetsDefend/images/20221229200554.png)  

## 2. Determine Suspicious Activity

![](/posts/LetsDefend/images/20221229201416.png)  

>Going to the [LolBas project](https://lolbas-project.github.io/lolbas/Binaries/Mshta/) we can see how mshta can be used for in a malicious manner
```
mshta.exe evilfile.hta
```

>Also we can check the MD5 Hash of the file from the Investigations page and upload it in [Virus Total](https://www.virustotal.com/gui/file/886095c7861a068d1ee603c71cb161f256941e802e743fe2161f30013947a2f1)

![](/posts/LetsDefend/images/20221229201900.png)  


## 3. What Is Suspicious Activity?

```
The suspicious activity we can see that is execution

Usecase: Execute code
Privileges required: User
OS: Windows vista, Windows 7, Windows 8, Windows 8.1, Windows 10, Windows 11
MITRE ATT&CK®: T1218.005: Mshta
```

## 4. Who Performed the Activity?

![](/posts/LetsDefend/images/20221229203100.png)  

>Since the parent process is explorer, the user did the activity

## 5. Containment

>Since there is a malicious activity that took place on the machine it means the machine could be compromised. We have to contain the machine.

## 6. Adding Artifacts 

![](/posts/LetsDefend/images/20221229203416.png)  


>Since we have the known hash of the file, it is recommended that we add this to our artifacts. 
From the command history we could also see that the script tried to contact a C2 server on 193[.]142[.]58[.]23


![](/posts/LetsDefend/images/20221229203848.png)  
![](/posts/LetsDefend/images/20221229204006.png)  


## 7. Close the Alert


>This is the end of this investigation. After you close the investigation you can see in closed alerts how you did.
