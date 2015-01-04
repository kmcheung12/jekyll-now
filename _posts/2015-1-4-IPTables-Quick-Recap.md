---
layout: post
tags: iptables, centos
title: CentOS iptables quick reference
---

One thing I deal with oftenly during deployment of MongoDB is the CentOS built-in firewall, iptables.  
  
This post is a short reminder for myself about terminologies and commands used in iptables.  

## Terminology

### Table
So far I have only used the default table `filter` 
  
### Chain
Place where rules are placed.  
3 predefined chains on `filter` table (may have different chains on different table):  

- INPUT - packets coming into the host computer
- OUTPUT - packets going out from the host computer
- FORWARD - packets routed by the host computer

### Target
Action applied on packet when it reached the chain.
Common targets:  

- ACCEPT - Let packet go through
- DROP - Drop packet, no message returned
- REJECT - Drop packet, with message acknowledging other end

### Policy
Default action on packets, usally either ACCEPT or DROP

## Command Example
1. `iptables -P INPUT ACCEPT`    
switch default policy of chain `INPUT` to `ACCEPT`. Useful when planning to change firewall setting remotely. Prevent blocking yourself from firewall by subsequent iptables update.

2. `iptables -A INPUT -p tcp --dport 22 -j ACCEPT`  
Allow tcp connection over port 22

### Reference
[http://wiki.centos.org/HowTos/Network/IPTables](http://wiki.centos.org/HowTos/Network/IPTables)