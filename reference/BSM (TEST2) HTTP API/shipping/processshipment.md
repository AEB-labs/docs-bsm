---
title: processShipment
excerpt: >-
  Allows to add packages or perform various operations on an existing shipment.
  Especially document preparation and document (label) output can be
  triggered.<br> When the request is specified to handle the operations
  asynchronously, operation processing errors and label documents are not part
  of the response. They can be retrieved with a <code>syncShipments</code> or
  <code>getShipments</code> call.
api:
  file: openapi_v3.json
  operationId: processShipment
hidden: false
---