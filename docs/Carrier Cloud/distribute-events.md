---
title: Distribute Events
deprecated: false
hidden: false
metadata:
  robots: index
---
## Shipment creation

In some system landscapes, one system (e.g., SAP EWM) must initiate carrier shipment creation, while tracking events for those shipments are synchronized to another system (e.g., SAP ERP).

For this use case, Business Service Management provides the `createShipment` API from Carrier Connect, extended with details about the target system and target business object (e.g., SAP delivery):

<Table>
  <thead>
    <tr>
      <th>
        Technique
      </th>

      <th>
        Documentation
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        REST
      </td>

      <td>
        <Anchor label="createShipment" target="_blank" href="https://rz3.aeb.de/test2bsm/swagger/#/BSM%20Carrier/createShipment">createShipment</Anchor>
      </td>
    </tr>

    <tr>
      <td>
        SOAP
      </td>

      <td>
        <Anchor label="BSMCarrierBF (WSDL)" target="_blank" href="https://rz3.aeb.de/test2bsm/servlet/bf/BSMCarrierBF?WSDL">BSMCarrierBF (WSDL)</Anchor> |
        <Anchor label="createShipment (Java Doc)" target="_blank" href="https://rz3.aeb.de/test2bsm/servlet/bf/doc/BSMCarrierBF/de/aeb/xnsg/bsm/carrier/bf/IBSMCarrierBF.html#createShipment(de.aeb.xnsg.bsm.carrier.bf.create.BSMDLCreateShipmentRequestDTO)">createShipment (Java Doc)</Anchor>
      </td>
    </tr>
  </tbody>
</Table>

The following shows an example call for this scenario. It matches the standard `createShipment` API of Carrier Connect, with only the `interactionControls` field added. This field contains two pieces of information.

* usecaseId: in this case "CES_EVENT_DATA"
* ids:
  * boIdClientSystem: ID of the target business object in the backend ERP system
  * clientSystemId: ID of the backend ERP system

The IDs are required to link the event data (tracking data) to the business object in the target system. 

Lets assume we an example scenario with two systems: 

*  An EWM system with system ID "JNH" and client 080. This EWM system sends the shipment data to Carrier Cloud. The outbound delivery order in EWM is 80000123, same as the linked outbound delivery in ERP.
* An ERP system with system ID "E01" and client 400. This ERP system will receive (synchronize) the tracking events. The data shall be linked to the outbound delivery. 

With these assumptions, the createShipment call from EWM will look like as follows:   

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:de.aeb.xnsg.bsm.carrier.bf">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:createShipment>
         <request>
             <interactionControls>
               <usecase><usecaseId>CES_EVENT_DATA</usecaseId></usecase>
               <ids>
               <boIdClientSystem>SAP_80000123</boIdClientSystem>
               <clientSystemId>SAP_E01_400</clientSystemId>
               </ids>
            </interactionControls>
 						<clientSystemId>SAP_EWM_JNH_080</clientSystemId>
            <clientIdentCode>ATC_TEST</clientIdentCode>
            <userName>JAM</userName>
            <resultLanguageIsoCodes>DE</resultLanguageIsoCodes>
            <creationParms>
               <creationMode>ALWAYS</creationMode>
            </creationParms>
            <shipment>
               <transactionId>SAP_EWM_JNH_080_OUTBOUND_DELIVERY_80000123</transactionId>
               <transactionLabel>80000123</transactionLabel>
               <organizationUnitClientSystem>DEFAULT</organizationUnitClientSystem>

               <isDocumentShipment>false</isDocumentShipment>
               <referenceNumber1>80000123</referenceNumber1>
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

## Subscription

To synchronize the tracking data back to SAP ERP,  maintain a subscription in BSM for the object _VCP-Consignment_. Assuming the shipping order was created in the EWM system with the installation ID ‘SAP_EWM_JNH_080’.
The ERP system will synchronize all the the data with installation ID ‘SAP_ERP_E01_400’.
Therefore, enter ‘SAP_ERP_E01_400’ in the field ‘Installation ID’ and “SAP_EWM_JNH_080” in the field ‘Source Installation ID’.
