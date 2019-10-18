# ArchitectureExample
Discusses how to build out a azure architecture for a mock ticketing application.

# Regions

For this example, we are going to create resources that will be created across the following regions:
1. West US 2
1. Central US

NOTE: when creating this example using a development subscription, not all of the regions were activated and best practice pairings could not be created.  In the future, the following pairings should be considered:

https://docs.microsoft.com/en-us/azure/best-practices-availability-paired-regions

# Resource Group
For now, this entire example will be created under one resource group to aide in its deletion.  While a resource group is required to be assigned a single region, resources that are assigned to the resource group can assigned different regions.  It is usually best practice to group resources together.  

Note, this may be revisited at a later date as this example matures in size and complexity.

## Creation of the Resource Group

Create a resource group named GX-NOTPROD-DEV.  Assign the region to be West-US-2.  

# Azure Front Door Setup

All the website traffic will be setup to run through azure front door.  

## Overview

Azure front door is an [Application Delivery Network](https://en.wikipedia.org/wiki/Application_delivery_network) as a service that provides layer 7 load balancing. Layer 7 load balancing enables application delivery controllers the ability to inspect traffic and gain deep insights into the application requests.  These insights allow for the controllers to rewrite context, perform security inspections, and implement access controls in addition to providing load balancing capabilities.  

Layer 7 load balancing enables ADC (Application Delivery Controllers) to redirect traffic more intelligently by inspecting content to gain deeper context on the application request. This additional context allows the ADC to not only optimize load balancing but to also rewrite content, perform security inspections and to implement access controls.


### Benifits of Using Azure Front Door 

The following outline the benefits of using azure front door over the use of a traffic manager. 

#### Benifits of Using Azure Front Door over Traffic Manager



HTTP acceleration - traffic is proxied at the edge of Microsoft's Network.  Http/Https latency is decreased and throughput is increased. 



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

<a id="GlossaryApplicationDeliveryController"></a>Application Delivery Controller - An application delivery controller (ADC) is a computer network device in a datacenter, often part of an application delivery network (ADN), that helps perform common tasks, such as those done by web accelerators to remove load from the web servers themselves. Many also provide load balancing.
