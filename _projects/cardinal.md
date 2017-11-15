---
layout: page
title: Opendaylight-Cardinal
date: {}
permalink: /cardinal/
categories: sdn
desc: Opendaylight monitoring as a Service
published: true
---

**Technologies** : Java,Maven,Karaf,Jenkins,Opendaylight,SDN

**Duration** : March-2015 to August-2016

**Repository** : [https://github.com/opendaylight/cardinal](https://github.com/opendaylight/cardinal)

**LOC committed** : [https://github.com/opendaylight/cardinal/graphs/contributors](https://github.com/opendaylight/cardinal/graphs/contributors)

**Project Proposal** : [https://wiki.opendaylight.org/images/8/89/Cardinal-ODL_Monitoring_as_a_Service_V2.pdf](https://wiki.opendaylight.org/images/8/89/Cardinal-ODL_Monitoring_as_a_Service_V2.pdf)

---
In current legacy network, NMS (Network Management Systems) is a viable approach to provide a centralized system that monitors and controls remote/managed devices located throughout the network, using for examplle SNMP (the basic protocol). Of-course there are others protocol like TL1, TMF/Corba that are also being leveraged to monitor the managed network.

With the advent of Software Defined Networks, the basic need arises to monitor the network (Controller, deployed features, network etc.). As a first step, on priority the need arises to expose the SDN Controller' (OpenDaylight) health/statistics to existing legacy NMS applications. With SDN networks yet to provide inter-working for monitoring/management functionality, the need arises to at least enable the NMS operators to get access to health/diagnostics information from/of SDN Controller.

![Cardinal2.PNG]({{site.baseurl}}/assets/Cardinal2.PNG)

Cardinal (OpenDaylight Monitoring as a Service) proposes a solution in OpenDaylight that extends the following for a remote NMS:

- OpenDaylight MIB (Management Information Base) defined in OID experimental
- Enable ODL diagnostics to be exposed across SNMP for remote NMS
- Integrate with OpenDaylight TSDR and Centinel for monitoring data and analytics
- Extend ODL diagnostics across northbound for autonomous notifications (SNMP Traps)



**Cardinal feature (Karaf support)**

- Run snmpd/snmptrapd daemon in background once the Cardinal feature is turned on
- Supported SNMP commands - snmpwalk, snmpget, snmptranslate, snmpgetnext
- SNMP Autonomous events (INFO & Traps) will be supported



**Cardinal Core ODL Data**

- Introduce SNMP OID for OpenDaylight monitoring/inter-working to remote/legacy NMS
- Support ODL diagnostics – ex: ODL health (CPU, Memory usage, up time etc.)
- Support autonomous notifications - ODL SNMP Traps and INFO messages
- Interacts with Karaf using SSH or REST APIs (if available)
- Interacts with MD-SAL to store relevant data into datastore



**Cardinal REST APIs**

- Support REST GET equivalent to SNMP GET requests - to enable SDN Applications to retrieve ODL diagnostics
- POST to start/stop daemon


**B**eing the initial committer, I started the building of project from scratch and committed 16k lines of code in Opendaylight to support the overall functionalitied of Cardinal.

---
