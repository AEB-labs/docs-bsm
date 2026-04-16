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
This is really the main part. Transferring all the business object which are relevant for O&P.

* addresses (Customers,Vendors)
* materials
* bill of materials
* sales orders
* purchase orders
* goods receipts

The APIs we provide for those data transfer are bulk-APIs. **VERY IMPORTANT**. You should not transfer more than **10** objects per API-Call. Otherwise you could run into timeouts.

When we look into the transfer-APIs there always the following fields for one business object:

* idHost: this has to be unique for one client in combination with the organizational unit.
* isDeleted: If the object should be deleted, this is always possible over this flag
* labelHost: in addition to idHost a readable id
* organizationalUnit: used to differ between orginazational units, if not filled "DEFAULT" is used.

Also each transfer request needs some basic information:

* clientIdentCode: The identcode of the client in BSM
* clientSystemId: The id of the calling system
* resultLanguages: the given languages are used for error messages
* userName: gibt the API-Call an functional user, this is not a user for authentifcation
