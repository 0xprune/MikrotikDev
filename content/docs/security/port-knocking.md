---
weight: 350
title: "Port Knocking"
description: ""
icon: "lock"
date: "2023-08-26T20:43:23+01:00"
lastmod: "2023-08-26T20:43:23+01:00"
aliases:
    - ../guides/security
draft: false
toc: true

---

```
/ip firewall filter
add action=accept chain=input comment="Port Knocking Security" connection-state=established,related
add action=add-src-to-address-list address-list=Temporary address-list-timeout=1m chain=input dst-port=1234 protocol=tcp
add action=add-src-to-address-list address-list=Valid address-list-timeout=1m chain=input dst-port=4321 protocol=tcp src-address-list=Temporary
add action=accept chain=input src-address-list=Valid
add action=drop chain=input
```