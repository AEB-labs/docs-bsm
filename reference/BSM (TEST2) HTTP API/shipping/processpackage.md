---
title: processPackage
excerpt: >-
  Allows to perform various operations on an existing package. Especially
  document preparation and document (label) output can be triggered.<br> When
  the request is specified to handle the operations asynchronously, operation
  processing errors and label documents are not part of the response. They can
  be retrieved with a further <code>processPackage</code> call, a
  <code>syncShipments</code> or <code>getShipments</code> call.
api:
  file: openapi_v3.json
  operationId: processPackage
hidden: false
---