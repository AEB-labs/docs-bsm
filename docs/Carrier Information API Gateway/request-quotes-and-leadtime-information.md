---
title: Request quotes and leadtime information
excerpt: >-
  The service "Carrier Information API Gateway" provides carrier related
  information, e.g. runtimes and freight charges. 
deprecated: false
hidden: false
metadata:
  robots: index
---
Legal disclaimers for using the API

All API responses include important notices stating that freight costs and transit times may not be used for comparison with other service providers. This is a legal requirement for using the gateway.

AEB refers to the clearly formulated information in the service descriptions and notes in the API responses. The responsibility for compliance with carrier conditions lies with the customer. Individual customer solutions are outside of AEB responsibility.

## getQuotes

With the getQuotes API call, one can retrieve quoted freight charges and lead times based on the data sent in the request. This API call does not require an existing shipping order in Carrier Connect, differently to the "getShipment"-API.

The call has two parameters on header level: 

* shipment - see [ShipmentRequestDataDTO](https://rz3.aeb.de/test1bsm/servlet/bf/doc/DLCarrierBF/de/aeb/xnsg/dl/bf/DLShipmentRequestDataDTO.html) 
* shippingTime  - Format: HH:MM:SS 

<br />

```Text JSON
{
	"clientSystemId": "Host System Name",
	"clientIdentCode": "Carrier Connect Client Name",
	"userName": "User Name",
	"resultLanguageIsoCodes": [
		"de"
	],
	"creationParms": {
		"creationMode": "VALIDATION_OK"
	},
	"processParms": {
		"processMode": {
			"mode": "EXTENDED"
		},
		"documentPrepareScope": {
			"scope": "ALL"
		},
		"workstationId": "ZPL203_A4LASER",
		"documentOutputScope": {
			"scope": "ALL"
		},
		"documentOutputMode": {
			"mode": "RETURN"
		},
		"doCompletion": true
	},
	"shipment": {
		"transactionId": "516513219",
		"referenceNumber1": "1000001",
		"carrierIdentCode": "GENERICCARRIER",
		"serviceCode": "STD",
		"termsOfDeliveryCode": "EXW",
		"contents": "spare parts",
		"shippingDate": "2025-01-10",
		"shippingPt": {
			"city": "Stuttgart",
			"companyNumber": "1000",
			"countryISOCode": "DE",
			"name": "AEB SE",
			"postcode": "70567",
			"street": "Sigmaringer Straße 109"
		},
		]
	}
```

<br />

<br />
