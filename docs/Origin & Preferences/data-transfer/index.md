---
title: Data Transfer
deprecated: false
hidden: false
metadata:
  robots: index
next:
  description: Start with your first business object the addresses.
  pages:
    - slug: transfer-addresses
      title: Transfer Addresses
      type: basic
---
For the calculation and handling of preferences, certain business objects are required:

* addresses (customers and vendors)
* materials
* bill of materials
* sales orders
* purchase orders
* goods receipts

The available APIs for transferring these data objects are bulk-APIs.

**Please note**. You should not transfer more than **10** objects per API-Call. Otherwise time outs can occur.

Looking into the APIs for data transfer, there are always the following fields for each business object:

* idHost: this has to be unique for one client in combination with the organizational unit.
* isDeleted: If the object should be deleted, this is always possible over this flag
* labelHost: in addition to idHost a readable id
* organizationalUnit: used to differ between orginazational units, if not filled "DEFAULT" is used.

Also each transfer request needs to have some basic information:

* clientIdentCode: the identcode of the client in BSM
* clientSystemId: the id of the calling system, e.g. SAP_P01_400 
* resultLanguages:  list of languages - responses are returned in theses languages 
* userName: the business user working with the application (not a user for authentification)
