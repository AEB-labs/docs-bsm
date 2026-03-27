---
title: Distribute Events
deprecated: false
hidden: false
metadata:
  robots: index
---
There is the requirement that one System (e.g. SAP EWM) starts with creating an carrier shipment, but the events for those shipments should be synchronized to another System (e.g. SAP ERP). For this usecase the Business Service Management offers the createShipment API of Carrier Connect extended with information about the target System and target business object (e.g. SAP delivery).

In the follwing there is an example call for this usescase. Everything is the same as in the createShipment API of carrier connect only the field interactionControls is added. Those controls have two informations.

* usecaseId: in this case CES_EVENT_DATA
* ids:
  * boIdClientSystem: id of the target business object for the event data
  * clientSystemId: id of the system for the event data

Those informations are needed to distribute the event data to the target object/system.

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:de.aeb.xnsg.bsm.carrier.bf">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:createShipment>
         <request>
             <interactionControls>
               <usecase><usecaseId>CES_EVENT_DATA</usecaseId></usecase>
               <ids>
               <boIdClientSystem>SAP_ERP_ID_05</boIdClientSystem>
               <clientSystemId>SAP_ERP_E01</clientSystemId>
               </ids>
            </interactionControls>
 						<clientSystemId>SAP_JNH_080</clientSystemId>
            <clientIdentCode>ATC_TEST</clientIdentCode>
            <userName>JAM</userName>
            <resultLanguageIsoCodes>DE</resultLanguageIsoCodes>
            <creationParms>
               <creationMode>ALWAYS</creationMode>
            </creationParms>
            <shipment>
               <transactionId>SAP_JNH_080_OUTBOUND_DELIVERY_80000061</transactionId>
               <transactionLabel>SAP_EWM_ID_05</transactionLabel>
               <organizationUnitClientSystem>DEFAULT</organizationUnitClientSystem>

               <isDocumentShipment>false</isDocumentShipment>
               <referenceNumber1>80000061</referenceNumber1>
          	<termsOfDeliveryCode>FCA</termsOfDeliveryCode>     
               <remark>remark</remark>
               <shippingDate></shippingDate>
               <contents>all</contents>
               <shippingPt>
                  <companyNumber>1010</companyNumber>
                  <name>SP 1010</name>
                  <street>blubstr 10</street>
                  <postcode>71088</postcode>
                  <city>Blubber</city>
                  <countryISOCode>DE</countryISOCode>
               </shippingPt>
               <consignee>
                  <companyNumber>1650</companyNumber>
                  <name>Henderson Inc</name>
                  <street>Markostra 5</street>
                  <postcode>71088</postcode>
                  <city>Holzegrlingen</city>
                  <countryISOCode>DE</countryISOCode>
                  </consignee>
               <carrierIdentCode>UPS</carrierIdentCode>
               <serviceCode>UPS_EXPR</serviceCode>
               <goodsValue>
                  <value>100</value>
                  <currencyIso>EUR</currencyIso>
               </goodsValue>
               <invoiceValue>
                  <value>100</value>
                  <currencyIso>EUR</currencyIso>
               </invoiceValue>
               <shipmentTotals>
                  <numberOfPackagesExpected>1</numberOfPackagesExpected>
                  <grossWeightExpected>
                     <value>0.5</value>
                     <unit>gr</unit>
                  </grossWeightExpected>
                  </shipmentTotals>
               <packages>
                  <packageTypeIdentCode>CI</packageTypeIdentCode>
                  <packageSpecificeContents></packageSpecificeContents>
                  <packageNumber>123</packageNumber>
                  <packageTransactionId>565</packageTransactionId>
                  <referenceNumber1>8888</referenceNumber1>
                  <grossWeight>
                     <value>100</value>
                     <unit>gr</unit>
                  </grossWeight>
                  <dimensions>
                     <length>10</length>
                     <width>10</width>
                     <height>10</height>
                     <identCode>cm</identCode>
                  </dimensions>              
               </packages>
            </shipment>
            <processParms>
               <processMode>
                  <mode>BASIC</mode>
               </processMode>
               <documentPrepareScope>
                  <scope>NONE</scope>
               </documentPrepareScope>
               <workstationId>JAM</workstationId>
               <documentOutputScope>
                  <scope>NONE</scope>
               </documentOutputScope>
               <documentOutputMode>
                  <mode>NONE</mode>
                  <includeDocumentId></includeDocumentId>
                  <includeContent></includeContent>
               </documentOutputMode>
               <doCompletion>false</doCompletion>
            </processParms>           
         </request>
      </urn:createShipment>
   </soapenv:Body>
</soapenv:Envelope>
           
```
```json
{
  "clientSystemId": "SAP_JNH_080",
  "clientIdentCode": "API_TEST",
  "userName": "User Name",
  "resultLanguageIsoCodes": [
    "en"
  ],
  "interactionControls": [
    {
      "usecase": {
        "usecaseId": "CES_EVENT_DATA"
      },
      "ids": [
        {
          "boIdClientSystem": "SAP_ERP_ID_05",
          "clientSystemId": "SAP_ERP_E01"
        }
      ]
    }
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
    "shippingPtContact": {
      "name": "AEB Support",
      "phone": "+49 711 72842 110"
    },
    "consignee": {
      "city": "München",
      "companyNumber": "2000",
      "countryISOCode": "DE",
      "name": "AEB München",
      "postcode": "81249",
      "street": "Franz-Josef-Delonge-Strasse 7"
    },
    "consigneeContact": {
      "name": "AEB Empfang München",
      "phone": "0891490267-0"
    },
    "goodsValue": {
      "currencyIso": "EUR",
      "value": 1000
    },
    "items": [
      {
        "itemTransactionId": "100015681352",
        "referenceNumber1": "1000-1",
        "description": "Item #1 description",
        "goodsValue": {
          "currencyIso": "EUR",
          "value": 100
        },
        "grossWeight": {
          "unit": "kg",
          "value": 6
        },
        "quantity": {
          "unit": "St",
          "value": 10
        }
      }
    ],
    "packages": [
      {
        "packageTransactionId": "77702167",
        "packageTypeIdentCode": "PAL",
        "grossWeight": {
          "unit": "kg",
          "value": 6.25
        },
        "dimensions": {
          "length": 10,
          "width": 10,
          "height": 10,
          "identCode": "cm"
        }
      }
    ]
  }
}
```

<br />
