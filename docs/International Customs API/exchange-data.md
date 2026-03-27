---
title: Exchange Data
deprecated: false
hidden: false
icon: far fa-house-medical
metadata:
  robots: index
---
There are two usecases where data between Customs Management and other business services has to be exchanged:

* Paperless Trade in context of Carrier Connect
* Approvals in context of Export Controls

For those usecases the Business Service Managment offers an extended createConsignment-API. 

The API is extended by information about the transaction of the processed mentioned before.

There are two usecase-Ids:

* EC_APPROVAL_DATA for data exchange in context of Export Controls approvals
* CCO_SHP_CUSTOMS_UPD for data exchange in context of Carrier Connect and Paperless Trade

The CreateShipment-API call could the look like the following. 

```xml
<interactionControls>
   <useCaseId>EC_APPROVAL_DATA</useCaseId>
	<boIdClientSystem>SAP_JNH_080_OUTBOUND_DELIVERY_80000061$DEFAULT</boIdClientSystem>
	<clientSystemId>PGTEST1BSM_ATC_TEST</clientSystemId>
	<boItemIdClientSystem>10</boItemIdClientSystem>
</interactionControls>
```
```json
"interactionControls": [
      {
        "usecase": {
          "usecaseId": "string"
        },
        "ids": [
          {
            "boIdClientSystem": "string",
            "clientSystemId": "string"
          }
        ]
      }
    ]
```

<br />
