---
layout: page
title: OpenflowPlugin
date:
  'Fri Nov 25 2016 14:13:59 GMT+0530 (IST)': null
permalink: /openflowplugin/
categories: sdn
desc: Eviction and Vacancy Features in OpenFlowPlugin
published: true
---

**Technologies** : Java,Karaf,OpendFlowplugin,maven,Jenkins

**Official Repository link** : [openflowplugin](https://github.com/opendaylight/openflowplugin)

**Duration** : August-2015 to December-2015

---
OpenFlowplugin is the Southbound plugin of opendaylight controller. It is the mediator with parses the openflow protocol messages to and from the controller to openflow devices.

### The Use case(originally given by Ericsson):

- Various flows with different priority values are not hit or used in a given period of time. 
- Matching in sequential order, the flows with lower priority which are not used or hit can be pushed down the order.
- Eventually these flows can also be evicted from the table. 
- This way matching of the flows at Network Devices can be optimized and hence accounting to Adaptive and Optimized SDN Networking.


**A**s part of this activity I was resposible for delivering the eviction and vacancy features in Openflowplugin, which were already contributed to openvswitch by my colleagues in TCS. 

**What is Eviction and Vacancy?**

Eviction is mechanism of a switch to evict the low priority flows and allow the higher priority flows to get forwarded to table. In a certai


**Eviction Algorithm**

- Most flow tables have finite capacity.

- In previous versions of the specification, when a flow table is full, new flow entries are not inserted and an error is returned to the controller.

- Reaching that point is pretty problematic, as the controller need time to operate on the flow table and this may cause service down time.

- Eviction adds a mechanism enabling the switch to automatically eliminate entries of lower importance to make space for newer entries. 

- Table-mod flag OFPTC_EVICTION to enable or disable eviction on a table.

- Flow-mod importance to optionally denote the importance of a flow entry for eviction.

- Table-desc eviction property ofp_table_mod_prop_eviction to describe the type of eviction performed by the switch.

- Options for Type of eviction as sent by switch in OFPMP_TABLE_DESC reply.
	- OFPTMPEF_OTHER : the eviction process will use other factors, such as internal constraints, to perform eviction
	- OFPTMPEF_IMPORTANCE : the eviction process will use the flow entry importance field.
	- OFPTMPEF_LIFETIME : the eviction process will use the flow entry remaining lifetime, the shortest time to expiration

**Vacancy Events Algorithm**

- Vacancy events add a mechanism enabling the Controller to get an early warning based on a capacity threshold chosen by the Controller.

- This allows the controller to react in advance and avoid getting the table full.

- Switch will send Table status event OFPT_TABLE_STATUS with reasons OFPTR_VACANCY_DOWN and OFPTR_VACANCY_UP to inform Controller of vacancy change.

- The Controller can program two different vacancy threshold levels:    
                       vacancy_down and vacancy_up.

- Table-mod vacancy property to set vacancy thresholds:    
                       ofp_table_mod_prop_vacancy.

- When the table state changes, the controller needs to be informed with the OFPT_TABLE_STATUS message.

- The reason values OFPTR_VACANCY_DOWN and OFPTR_VACANCY_UP identify a vacancy message.

- The vacancy events are generated when the remaining space in the flow table changes and crosses one of the vacancy threshold.

- The fields vacancy_down and vacancy_up are the threshold for generating vacancy events that should be configured on this flow table, expressed as a percent.

- These fields are configured while sending TABLE_MOD message in the ofp_table_mod_prop_vacancy.


**I** submitted a patch([link](https://git.opendaylight.org/gerrit/#/c/28314/)) with the code to implement the above algorithms but unfortunaltely it was not merged and abandoned later, but it was a great experience learning the core features of a switch and how it same can be done from the Opendaylight perspective.

![]({{site.baseurl}}/assets/download.gif)
---
