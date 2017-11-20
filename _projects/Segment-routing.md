---
layout: page
title: Segment Routing
date:
  'Sat Sep 10 2016 14:13:59 GMT+0530 (IST)': null
permalink: /project/
categories: sdn
desc: A web application to demonstrate the capabilities of Segment Routing
published: true
---

---
### Flask Based Application to Demonstrate Segment Routing Solution in Real Network.
---

**Technologies**: Python,Ansible,Flask web framework, Segment Routing

**Link**: [http://www.segment-routing.net/](http://www.segment-routing.net/)

**Duration**: December-2016 to march-2017

---

**S**egment Routing is a key differentiator in cisco SP networking and architecture. It a Destination based routing which uses mpls labels to define your network paths.Like in MPLS, Segment Routing is based on label switching but with no extra protocol just extensions to the IGP (ISIS/OSPF).
Labels are called segments where we have the traditional Push, Swap, Pop actions. As part of this project, I developed an application to describe what Segment routing is and what capabilities it offers in a Service Provider's Network. The application provides an articulated demo flow structure to explain Segment routing. The applicaiton can successfully demostrated the following use cases:

- **SR configuration**: Demonstrate how easy is to add and validate SR and SR TE across the network

- **SR Tunnels**: Build on the ”SR configuration” use case, demonstrating the creation of dynamic and explicit SR tunnels

- **Multi-Domain PCE**: Use Cisco XTC as PCE to calculate and end to end dynamic tunnel path

- **SR & LDP**: Add SR to an existing LDP network and spread SR coverage thought the network without breaking current services


My major responsibilties while developing the application were as below:

- Implementation of an algorihm to trace the tunnel path in segment routing dynamic and explicit path tunnel use case.

- Implement the code for the above developed algorithm.

- Design the lab to build and showcase the Demonstration.

- Make the application smart by making the application as stage aware application which can be done using the finte state autometa. Python has a nice library to to implement finite state autometa([link](https://www.python-course.eu/finite_state_machine.php))

- Implement multithreaded module of python to make application faster and robust.

### Relevant Links

Official website: [http://www.segment-routing.net/](http://www.segment-routing.net/)

[Segment routing based traffic engineering for energy efficient backbone networks](http://ieeexplore.ieee.org/document/7057272/?reload=true)

[cisco's guide to introduction to Segment Routing](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/seg_routing/configuration/xe-3s/segrt-xe-3s-book/intro-seg-routing.pdf)

---
