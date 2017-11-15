---
layout: page
title: 'NEMO:Intent Base Networking'
date:
  'Fri Jan 01 2016 14:13:59 GMT+0530 (IST)': null
permalink: /intent/
categories: sdn
desc: Opendaylight's Intent Based Networking Use case
published: true
---

**Technologies** : Java,Maven,Karaf,SDN,Intent Based Networking

**Duration** : March-2016 to May-2016

**Official Repository** : [Nemo](https://github.com/opendaylight/nemo)

**Use Case Document** : [Bandwidth On Demand](https://wiki.opendaylight.org/images/c/cd/BoD.pdf)

---

**N**EMO is OpenDaylight project based on Network Intent. With the advent of self healing networks Intent based networking is grooming up quickly. Recently Cisco declared its next generation Networking to be based on "**[The Network Intuitive](https://www.youtube.com/watch?v=NJF1Em5lMlU)**". You can say that it is surely one of the biggest breakthrough in Enterprise networking. It brings together all the latest networking innovations including SDN, virtualization, machine learning, model-based APIs, and many security related innovations into a closed loop system capable of identifying, predicting, and responding to business needs

**What is Intent Base Networking?**

To answer it shortly, it is an abstraction layer put over Networking to hide the complexities of the Network configuration. For a detailed definition please visit: [link](https://www.networkworld.com/article/3202699/lan-wan/what-is-intent-based-networking.html)


**What is NEMO?**

The North-Bound Interface (NBI), located between the controller and the applications/services, is essential to enable application innovations and to nourish the SDN ecosystem by abstracting the network capabilities/information and opening the abstract/logic network to applications. To implement a novel NBI design, we can learn from the successful case of SQL (Structured Query Language), which simplified complicated data operation into a unified and intuitive way in the form of language. Applications do not define the underlying mechanism for data storage and data operation; Applications only describe the expectation on the data storage and operation and then get the results. As a data domain DSL (Domain Specific Language), SQL is simple and intuitive, and can be embedded in applications. So what we need for the network NBI is a set of “network domain SQL”. NEMO language is a DSL based for the abstraction of network models and conclusion of operation patterns. It provides NBI fashion in the form of language. Instead of tons of abstruse APIs, with limited number of key words and expressions, NEMO language enables network users/applications to describe their demands for network resources, services and logical operations in an intuitive way. And finally the NEMO language description can be explained and executed by a language engine.

As a NBI language, NEMO has the following features:

### User/Application centric abstraction

To simply the operation, applications or users can use NEMO directly to describe their requirements for the network without taking care of the implementation. All the parameters without user concern will be concealed by the NBI.

### Consistent NBI model and pattern

While existing NBIs are proposed by use cases (e.g. virtual network, QoS, traffic engineering, service chaining), NEMO with consistent model and pattern is promising as easier to use and to extend for future proof applications.

### Intuitive to use

The expression of NEMO is human-friendly and can be easily understood by network developers. Using a language style NBI is more like the application talks to the network. Another advantage to use language is that its flexibility for northbound application developer.

### Platform independent

With NEMO, the application or user can describe network demands in a generic way, so that any platform or system can get the identical knowledge and consequently execute to the same result. Any low-level and device/vendor specific configurations and dependencies can be avoided. Any technology related network solution can be concealed. 


**The USE CASE: Bandwidth On Demand**

As you can see the document attached in the top of this blog for the detailed instruction on the use case , I implemented and showcased Bandwidth On demand Use case using opendaylight controller as part of the internal Proof of concept in Tata consultancy Services. The use case envolved defining rules for bandwidth in the form of intents or rules, than simulating network topology using mininet(mininet is network simulation tool to simulate nodes and experiment on their behavior on actual network) and than adjusting bandwidth using a python application.


![]({{site.baseurl}}/assets/download.gif)


---
