---
title: 'Determine freight costs for completed shipping orders  '
deprecated: false
hidden: false
metadata:
  robots: index
---
# getShipment API

For shipping orders already processed via Carrier Connect (e.g. after successful label printing), the associated freight costs can be determined. The calculated freight costs are based on the actual shipping order data transmitted.

The determined freight costs can be used for further processing, e.g.

* for cost control and post-calculation,
* for internal billing,
* for evaluations and analyses.

<br />

The API expects the following parameters:

* Reference - references for an existing shipping order in Carrier Connect. See  <Anchor label="ShpimentReferenceDTO" target="_blank" href="https://rz3.aeb.de/test1bsm/servlet/bf/doc/DLCarrierBF/de/aeb/xnsg/dl/bf/DLShipmentReferenceDTO.html">ShpimentReferenceDTO</Anchor>
* IncludeDocuments - indicates that documents should be returned - boolean (TRUE or FALSE)
* ShippingTime  - the expected time of shipping, in format HH:MM:SS

Example call:

```xml
<INCLUDEDOCUMENTS>false</INCLUDEDOCUMENTS>
<REFERENCE>
  <REFERENCENUMBER1>87650010</REFERENCENUMBER1> 
  <SHIPMENTNUMBER>5223</SHIPMENTNUMBER> 
</REFERENCE>
<SHIPPINGTIME>18:30:00</SHIPPINGTIME> 


```

<br />

<br />

<br />
