# Example Ticket System Architecture - Version 1
Discusses how to build out a azure architecture for a mock ticketing application.

# Regions

For this example, we are going to create resources that will be created across the following regions:
1. West US 2
1. Central US

NOTE: when creating this example using a development subscription, not all of the regions were activated and best practice pairings could not be created.  In the future, the following pairings should be considered:

https://docs.microsoft.com/en-us/azure/best-practices-availability-paired-regions

# Web Sites

This example will host two websites:

www.exampleticketfd.com

www.exampletickettm.com

# Resource Group
For now, this entire example will be created under one resource group to aide in its deletion.  While a resource group is required to be assigned a single region, resources that are assigned to the resource group can assigned different regions.  It is usually best practice to group resources together.  

Note, this may be revisited at a later date as this example matures in size and complexity.

## Creation of the Resource Group

Create a resource group named GX-NOTPROD-DEV.  Assign the region to be West-US-2.  

# Azure Front Door 

By default, we will setup all the website traffic to run through azure front door by default.  In addition to using azure front door, this sample will also setup a traffic manager so users of this example can compre the differences.

## Overview

Azure front door is an [Application Delivery Network](https://en.wikipedia.org/wiki/Application_delivery_network) as a service that provides layer 7 load balancing. [Layer 7 load balancing](https://www.nginx.com/resources/glossary/layer-7-load-balancing/) enables application delivery controllers the ability to inspect traffic and gain deep insights into the application requests.  These insights allow for the controllers to rewrite context, perform security inspections, and implement access controls in addition to providing load balancing capabilities.  

Layer 7 load balancing enables ADC ([Application Delivery Controllers](#GlossaryApplicationDeliveryController)) to redirect traffic more intelligently by inspecting content to gain deeper context on the application request. This additional context allows the ADC to not only optimize load balancing but to also rewrite content, perform security inspections and to implement access controls.


### Benifits of Using Azure Front Door 

#### Benifits of Using Azure Front Door over Traffic Manager

The following outline the benefits of using azure front door over the use of a traffic manager. 

**HTTP acceleration** - traffic is proxied at the edge of Microsoft's Network.  Http/Https latency is decreased and throughput is increased. 

**Application Layer Processing** - Azure front door provides the ability to do url re-writing and provides a web application firewall.

**Prevents Stale DNS Entry Caching** - Prevents users from sent to stale DNS entries.

### Disadvantages of Using Azure Front Door

#### Disadvantages of Using Azure Front Door over Traffic Manager

Azure front door only works with HTTP, HTTPS and HTTP/2 as it operates at layer 7.

## Configuration

Setting | Value | Comments
------- | ----- | -------
Resource Group | GX-NOTPROD-DEV
Front End Host | gxapidev(.azurefd.net)
Session Afinity| No | We are not going to use this for now.  Later examples will.
Web Application Firewall | No | We are not going to use this for now.  Later examples will.

# SQL Server Setup

# Database Servers:
This example architecture is designed to have two databases named:
1. Create database gxnotproddb01 (westus2)
1. Create database gxnotproddb02 (centralUS)

## gxnotproddb01 Setup - WestUs2

Setting | Value
------- | -----
Resource Group | GX-NOTPROD-DEV
Server Name | gxnotproddb01
Server Login | (pick a login)
Server Password | (pick a password)
Location | West US 2
Connectivity Method | Public Endpoint
Allow Azure Reources to Access | True
Add Current Client IP | True


### Database Setup

Setting | Value
------- | -----
Database Name | Ticket


## gxnotproddb02 Setup - Central US
Setting | Value
------- | -----
Resource Group | GX-NOTPROD-DEV
Server Name | gxnotproddb02
Server Login | (pick a login)
Server Password | (pick a password)
Location | Central US
Connectivity Method | Public Endpoint
Allow Azure Reources to Access | True
Add Current Client IP | True

### Database Setup

Setting | Value
------- | -----
Database Name | Ticket

# Data Setup

# Model Cost Analysis

2 Database - Standard  - 15 a month.


# Simulating DB Failover

# Glossary

Application Instances

Application Slols

Azure Templates

<a id="GlossaryApplicationDeliveryController"></a>**Application Delivery Controller** - An application delivery controller (ADC) is a computer network device in a datacenter, often part of an application delivery network (ADN), that helps perform common tasks, such as those done by web accelerators to remove load from the web servers themselves. Many also provide load balancing.
