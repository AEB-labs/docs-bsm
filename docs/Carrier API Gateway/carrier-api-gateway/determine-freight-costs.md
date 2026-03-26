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

```json
{
  "clientSystemId": "ERP_SYSTEM_A",
  "clientIdentCode": "API_TEST_CLIENT",
  "userName": "AnyUserName",
  "resultLanguageIsoCodes": [
    "en"
  ],
  "reference": {
    "transactionId": "PR1     400008000026920251105101712JLO  1000",
    "referenceNumber1": "",
    "shipmentNumber": ""
  },
  "includeDocuments": false,
  "shippingTime": "12:00:00"
}
```
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:de.aeb.xnsg.bsm.carrier.bf">
    <soapenv:Header/>
    <soapenv:Body>
        <urn:getShipment>
            <requestDTO>
                <clientSystemId>PR1_400</clientSystemId>
                <clientIdentCode>{{client}}</clientIdentCode>
                <userName>{{user}}</userName>
                <resultLanguageIsoCodes>EN</resultLanguageIsoCodes>
                <reference>
                    <transactionId>PR1     400008000026920251105101712JLO  1000</transactionId>
                    <referenceNumber1/>
                    <shipmentNumber/>
                </reference>
                <includeDocuments>true</includeDocuments>
                <shippingTime>12:00:00</shippingTime>
            </requestDTO>
        </urn:getShipment>
    </soapenv:Body>
</soapenv:Envelope>


```

<br />

<br />

<br />
