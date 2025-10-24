---
title: Create custom APIs
excerpt: Modify the data using a custom api.
deprecated: false
hidden: false
metadata:
  robots: index
---
To modify data collected from the SAP System by us, you can hook your own custom API to our process and change all the data on the fly.

# Create API via ADT

Connect you cloud system to the ADT by creating a new project, entering the system URL and login. Then create a package.

## Create HTTP service

Create a new HTTP service via New -> Other -> HTTP Service

Fill the rest accordingly to create a inbound service.

## Create communication scenario

Create a new communication scenario via New -> Other -> Communication Scenario

Switch the tab on the bottom to 'Inbound' and enter your newly created service by using the 'browse' function.

## Publish API

Publish the communication scenario locally (top right). Then create a communication arrangement for the system with the BSM communication user.

# Write the code

To make writing the code more comfortable we created a template you can insert into your service class.

The template is copied to your clipboard if you click the buttons in the SAP AEB delivery collector profiles or the SAP Compliance check profiles (General).

Insert this code simply into the service class to comfortably change the supplied data in the afterStdFilling method.

```
Code to see
```

<br />
