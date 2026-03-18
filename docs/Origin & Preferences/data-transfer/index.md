---
title: Data Transfer
deprecated: false
hidden: false
metadata:
  robots: index
---
This is really the main part. Transferring all the business object which are relevant for O&P. 

* addresses (Customers,Vendors)
* materials
* bill of materials
* sales orders
* purchase orders
* goods receipts

The APIs we provide for those data transfer are bulk-APIs. **VERY IMPORTANT**. You should not transfer more than **50 **objects per API-Call. Otherwise you could run into timeouts. 

<br />
