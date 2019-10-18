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

### Database Setup

Setting | Value
------- | -----
Database Name | Ticket

# Data Setup

# Model Cost Analysis

2 Database - Standard  - 15 a month.


# Simulating DB Failover
