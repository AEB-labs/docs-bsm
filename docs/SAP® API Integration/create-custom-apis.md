---
title: Create a custom API
excerpt: >-
  To modify the data collected from the SAP system,  call a customized API and
  change data on the fly.
deprecated: false
hidden: false
metadata:
  robots: index
---
<br />

# Create the API via ADT

Connect your SAP cloud system to the ADT by creating a new project, entering the system URL and login. Then create a package.

## Create an HTTP service

Create a new HTTP service via New -> Other -> HTTP Service

Fill the rest accordingly to create a inbound service.

## Create a communication scenario

Create a new communication scenario via New -> Other -> Communication Scenario

Switch the tab on the bottom to 'Inbound' and enter your newly created service by using the 'browse' function.

## Publish the API

Publish the communication scenario locally (top right). Then create a communication arrangement for the system with the BSM communication user.

# Write the code

To make the coding more comfortable we created a template you can insert into your service class. Copy the template to your clipboard like this:  

* in the AEB delivery collector profile 
* in SAP Compliance check profile (general)

Insert this code simply into the service class to comfortably change the supplied data in the afterStdFilling method.
