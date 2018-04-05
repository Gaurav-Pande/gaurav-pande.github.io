---
layout: page
title:  "Docker Log Management System"
date:   2016-01-01 08:43:59
permalink: /other/
categories: mixed
desc: "An application for container based logging"
---

**Technologies**: Docker,Elastic Searcg,Fluentdb


---
# LogManagement

This small Project will let you deploy a Logging stack and monitors for the syslog messages coming from the cisco ios xr devices. This same repository can be used for visualizing the logging information of the various containers.This will be introduced in detailed in coming days.
All the components used in this repo is opensource. But you need to have is a cisco iosxr for testing this project.

## Stack Used

1. Fluentd
2. Elastic Search
3. Kibana


![Image](https://github.com/Gaurav-Pande/DockerLogManagement/blob/master/assets/fluentd.png)


## Technologies Used

1. Docker Compose.
2. Elastic Search.
3. Ansible


## What this repo will install in your system:

1. Fluentd Container
2. ELastic Search Container
3. Kibana Container
4. Ios XRV


## Pre-requisite:

1. Docker-compose
2. You must have a cisco ios xr image. On how to download a iosxr image from please follow the link:
 IOS XRv Vagrant box image installed on your host: https://xrdocs.github.io/application-hosting/tutorials/iosxr-vagrant- quickstart for step by step instructions

# Part1: Logging Ios Xr logs

## Steps Involved:

### Step1: Clone the repository

git clone https://github.com/Gaurav-Pande/DockerLogManagement.git

### Step2: Bring Ios Xr Image

Go to the project directory and run:

Vagrant up


CLI Output:

```
LogManagemnet$ vagrant up
Ignoring ffi-1.9.10 because its extensions are not built.  Try: gem pristine ffi --version 1.9.10
Ignoring nokogiri-1.6.3.1 because its extensions are not built.  Try: gem pristine nokogiri --version 1.6.3.1
Ignoring unf_ext-0.0.7.1 because its extensions are not built.  Try: gem pristine unf_ext --version 0.0.7.1
Bringing machine 'router' up with 'virtualbox' provider...
==> router: Resuming suspended VM...
==> router: Booting VM...
==> router: Waiting for machine to boot. This may take a few minutes...
    router: SSH address: 127.0.0.1:2222
    router: SSH username: vagrant
    router: SSH auth method: private key
==> router: Machine booted and ready!
==> router: Machine already provisioned. Run `vagrant provision` or use the `--provision`
==> router: flag to force provisioning. Provisioners marked to run always will still run.

==> router: Machine 'router' has a post `vagrant up` message. This is a message
==> router: from the creator of the Vagrantfile, and not from Vagrant itself:
==> router: 
==> router: 
==> router:     Welcome to the IOS XRv (64-bit) VirtualBox.
==> router:     To connect to the XR Linux shell, use: 'vagrant ssh'.
==> router:     To ssh to the XR Console, use: 'vagrant port' (vagrant version > 1.8)
==> router:     to determine the port that maps to guestport 22,
==> router:     then: 'ssh vagrant@localhost -p <forwarded port>'
==> router: 
==> router:     IMPORTANT:  READ CAREFULLY
==> router:     The Software is subject to and governed by the terms and conditions
==> router:     of the End User License Agreement and the Supplemental End User
==> router:     License Agreement accompanying the product, made available at the
==> router:     time of your order, or posted on the Cisco website at
==> router:     www.cisco.com/go/terms (collectively, the 'Agreement').
==> router:     As set forth more fully in the Agreement, use of the Software is
==> router:     strictly limited to internal use in a non-production environment
==> router:     solely for demonstration and evaluation purposes. Downloading,
==> router:     installing, or using the Software constitutes acceptance of the
==> router:     Agreement, and you are binding yourself and the business entity
==> router:     that you represent to the Agreement. If you do not agree to all
==> router:     of the terms of the Agreement, then Cisco is unwilling to license
==> router:     the Software to you and (a) you may not download, install or use the
==> router:     Software, and (b) you may return the Software as more fully set forth
==> router:     in the Agreement.
```

### Step3: Run docker compose

Go to the FEK directory(fluentd-Elastic-Kibana) and run

docker-compose up

CLI-output

```
FEK$ docker-compose up
Starting elasticsearch
Recreating fluentd
Starting kibana
Attaching to elasticsearch, fluentd, kibana
```


### Step4: Connect router to enable logging

ssh to the ios xr router image that we bring up in the step1.

ssh vagrant@localhost -p 2012

CLI-Output

```
LogManagemnet $ ssh vagrant@localhost -p 2014
Password: 


RP/0/RP0/CPU0:ios#
```

enable logging:

```
RP/0/RP0/CPU0:ios(config)#logging 127.0.0.1 port 24224
RP/0/RP0/CPU0:ios(config)#commit
Tue Jun 20 14:03:08.471 IST
RP/0/RP0/CPU0:ios(config)#
```

### Step5: Visualize the Logs

Goto to the Kibana dashboard at localhost:5601 and you can see the nice logs coming through.


#### Things to Do:

Write ansible playbook

---
