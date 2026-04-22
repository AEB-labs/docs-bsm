---
title: Data Transfer
deprecated: false
hidden: false
metadata:
  robots: index
next:
  pages:
    - slug: transfer-addresses
      title: Transfer addresses
      type: basic
---
## Available APIs

For the calculation and handling of preference information, certain business objects are required and can be transferred from your ERP system via API:

* addresses (customers and vendors)
* materials
* bill of materials
* sales orders
* purchase orders
* goods receipts

<br />

> ❗️ Limit when transferring multiple objects in a call
>
> The APIs for transferring the data objects are bulk-APIs. However, do not transfer more than **10** objects per API call. Otherwise time outs can occur.

<br />

## General fields  

Looking into the APIs for data transfer, there are always the following fields for each business object:

* idHost: this ID has to be unique per client in combination with the organizational unit
* labelHost:  an ID which is "readable" for the users,  as the idHost is more of a technical ID   
* isDeleted:  use this flag to delete an object
*  organizationalUnit: used to differentiate between organizational units. If not provided, "DEFAULT" is used a constant value.

Also each transfer request needs to have some basic information:

* clientIdentCode: the identcode of the client in BSM
* clientSystemId: the id of the calling system, e.g. "SAP_P01_400" 
* userName: the business user working with the application, e.g. "Jane Doe"  (not a user for authentification)
* resultLanguages:  list of languages - responses are returned in these languages
