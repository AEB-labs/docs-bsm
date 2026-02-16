---
title: 'Request pricing for a shipping order  '
excerpt: >-
  The service "Carrier Information API Gateway" provides carrier related
  information, e.g. runtimes and freight charges. 
deprecated: false
hidden: false
metadata:
  robots: index
---
# getShipment API

This API determines the pricing (freight charges) for a shipping order that already exists in Carrier Connect.

The API expects the following parameters:

* Reference - a unique reference to an existing shipping order in Carrier Connect. See  <Anchor label="ShpimentReferenceDTO" target="_blank" href="https://rz3.aeb.de/test1bsm/servlet/bf/doc/DLCarrierBF/de/aeb/xnsg/dl/bf/DLShipmentReferenceDTO.html">ShpimentReferenceDTO</Anchor>
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

## WSDL

WSDL can be downloaded here: <Anchor label="WSDL" target="_blank" href="https://rz3.aeb.de/test1bsm/servlet/bf/BSMCarrierBF?WSDL">WSDL</Anchor>

## Legal disclaimers for using the API

All API responses include important notices stating that freight costs and transit times may not be used for comparison with other service providers. This is a legal requirement for using the gateway.

AEB refers to the clearly formulated information in the service descriptions and notes in the API responses. The responsibility for compliance with carrier conditions lies with the customer. Individual customer solutions are outside of AEB responsibility.
