---
title: Create and update an AEB Delivery
deprecated: false
hidden: false
metadata:
  robots: index
next:
  pages:
    - slug: delete-aeb-delivery
      title: Delete AEB Delivery
      type: basic
---
Use the following API to create or update an AEB delivery.&#x20;

More details about the fields can be found in the interface description:  <Anchor target="_blank" href="https://docs.aeb.com/doc/cm-994054667-1045011595-en-US/t-1045011595-994054667-en-US">https://docs.aeb.com/doc/cm-994054667-1045011595-en-US/t-1045011595-994054667-en-US</Anchor>

| Protocol | Documentation                                                                                                                                                                                                                                                                                                                                                                                         |
| -------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| REST     | <Anchor target="_blank" href="https://rz3.aeb.de/test2bsm/swagger/#/AEB%20Delivery/updateDelivery">updateAEBDelivery</Anchor>                                                                                                                                                                                                                                                                         |
| SOAP     | <Anchor target="_blank" href="https://rz3.aeb.de/test2bsm/servlet/bf/AEBDeliveryBF?WSDL">AEBDeliveryBF (WSDL)</Anchor> \|<br /><Anchor target="_blank" href="https://rz3.aeb.de/test2bsm/servlet/bf/doc/AEBDeliveryBF/de/aeb/xnsg/bsm/core/bf/delivery/IAEBDeliveryBF.html#updateDelivery(de.aeb.xnsg.bsm.core.bf.delivery.update.UpdateAEBDeliveryRequestDTO)">updateAEBDelivery (Java Doc)</Anchor> |

Let's start directly with creating your first AEB delivery. Here is an example call:

```json
{
  "clientSystemId": "BRUYES",
  "clientIdentCode": "API_TEST_CLIENT",
  "userName": "SOMEONE",
  "resultLanguageIsoCodes": [
    "DE"
  ],
  "delivery": {
    "interactionControls": [
      {
        "usecase": {
          "usecaseId": "CCO_SHP_CUSTOMS_UPD"
        },
        "ids": [
          {
            "boIdClientSystem": "id_1",
            "clientSystemId": "ERP_1"
          }
        ]
      }
    ],
    "boIdClientSystem": "BRUYES_1",
    "boIdClientSystemLabel": "BRUYES_1",
    "deliveryNumber": "BRUYES_1",
    "deliveryType": "F8",
    "items": [
      {
        "interactionControls": [
          {
            "usecase": {
              "usecaseId": "EC_APPROVAL_DATA"
            },
            "ids": [
              {
                "boIdClientSystem": "id_1",
                "clientSystemId": "ERP_1",
                "boItemIdClientSystem": "ITM_1"
              }
            ]
          }
        ],
        "itemNumber": "1",
        "idClientSystem": "1",
        "itemDescription": "best food",
        "prefOriginCountry": "DE",
        "originCountry": "DE",
        "originRegion": "01",
        "orderNumber": "BUREYS_1",
        "orderItemNumber": "1",
        "invoiceIdClientSystem": "BRUYES_1",
        "goodsDescriptions": [
          {
            "language": "DE",
            "description": "Cool food"
          }
        ],
        "parties": [
          {
            "companyNumber": "1650",
            "country": "DE",
            "city": "Stuttgart",
            "cityPostBox": "71088",
            "county": "",
            "district": "",
            "fax": "",
            "phone": "",
            "email": "",
            "name1": "Henderson INc",
            "name2": "",
            "name3": "",
            "name4": "",
            "postCode": "",
            "postCodePostBox": "",
            "postBox": "",
            "type": "SH",
            "street": "",
            "street2": "",
            "contact": {
              "type": "",
              "forename": "",
              "surname": "",
              "email": "",
              "phone": "",
              "initials": ""
            }
          }
        ],
        "costs": [
          {
            "type": "PPR0",
            "value": "10",
            "currency": "EUR"
          }
        ],
        "quantities": [
          {
            "type": "BillingQuantity",
            "unit": "ST",
            "value": "10"
          }
        ],
        "classifications": [
          {
            "type": "ECCN",
            "classificationValue": "1232132"
          }
        ],
        "additionalFields": [
          {
            "type": "Type",
            "value": "VALUe"
          }
        ],
        "materialNo": "M-11"
      }
    ],
    "parties": [
      {
        "companyNumber": "1650",
        "country": "DE",
        "city": "Stuttgart",
        "cityPostBox": "71088",
        "county": "",
        "district": "",
        "fax": "",
        "phone": "",
        "email": "",
        "name1": "Henderson INc",
        "name2": "",
        "name3": "",
        "name4": "",
        "postCode": "",
        "postCodePostBox": "",
        "postBox": "",
        "type": "SH",
        "street": "",
        "street2": "",
        "contact": {
          "type": "",
          "forename": "",
          "surname": "",
          "email": "",
          "phone": "",
          "initials": ""
        }
      },
      {
        "companyNumber": "JAM_TEST1",
        "country": "DE",
        "city": "Stuttgart",
        "cityPostBox": "71088",
        "county": "",
        "district": "",
        "fax": "",
        "phone": "",
        "email": "",
        "name2": "",
        "name3": "",
        "name4": "",
        "postCode": "",
        "postCodePostBox": "",
        "postBox": "",
        "type": "SH",
        "street": "",
        "street2": ""
      }
    ],
    "persons": [
      {
        "type": "CONTACT",
        "forename": "jochey",
        "surname": "Dum",
        "email": "",
        "phone": "",
        "initials": ""
      }
    ],
    "costs": [
      {
        "type": "PPR0",
        "value": "10",
        "currency": "EUR"
      }
    ],
    "quantities": [
      {
        "type": "BillingQuantity",
        "unit": "ST",
        "value": "1"
      }
    ],
    "handlingUnits": [
      {
        "boIdClientSystem": "1",
        "referenceNoHandlingUnit": "1",
        "typeCode": "PKG",
        "typeUNECECode": "PKG",
        "referenceSourceObject": "1",
        "handlingUnitNumberFrom": "1",
        "handlingUnitNumberTo": "",
        "contentDescription": "ALL",
        "dimensionHeight": "1",
        "dimensionWidth": "1",
        "dimensionLength": "1",
        "dimensionQuantityUnit": "cm",
        "quantities": [
          {
            "type": "QUANT_TYPE",
            "unit": "ST",
            "value": "1"
          }
        ],
        "packedItems": [
          {
            "itemIdClientSystem": "1",
            "quantity": "1"
          }
        ],
        "packedHandlingUnits": [],
        "additionalFields": [
          {
            "type": "TYPE",
            "value": "VALUE"
          }
        ]
      }
    ],
    "additionalFields": [
      {
        "type": "TYPE",
        "value": "VALUE"
      }
    ],
    "transportMeans": [
      {
        "type": "BRUYES",
        "identification": "ID",
        "nationality": "DE",
        "code": "CDE",
        "transportModeCode": "ModeCode"
      }
    ],
    "deliveryDate": {
      "dateInTimezone": "2026-01-01 10:00:00",
      "timezone": "UTC"
    },
    "shippingDate": {
      "dateInTimezone": "2026-01-01 10:00:00",
      "timezone": "UTC"
    },
    "incotermIdentCode": "",
    "incotermDescription": "",
    "incotermDestination": "",
    "invoices": [
      {
        "invoiceNumber": "1",
        "boIdClientSystem": "1",
        "boIdClientSystemLabel": "1",
        "invoiceDate": {
          "dateInTimezone": "2026-01-01 10:00:00",
          "timezone": "UTC"
        }
      }
    ]
  },
  "mappingProfile": "BRUYES"
}
```
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:de.aeb.xnsg.bsm.core.bf.delivery">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:updateDelivery>
         <request>
            <clientSystemId>BRUYES</clientSystemId>
            <clientIdentCode>ATC_TEST</clientIdentCode>
            <userName>SOMEONE</userName>
            <resultLanguageIsoCodes>DE</resultLanguageIsoCodes>
            <delivery>
              <interactionControls>
                <usecase>
                  <usecaseId>CCO_SHP_CUSTOMS_UPD</usecaseId>
                </usecase>
                <ids>
                  <boIdClientSystem>id_1</boIdClientSystem>
                  <clientSystemId>ERP_1</clientSystemId>
                </ids>
              </interactionControls> 
              <boIdClientSystem>BRUYES_1</boIdClientSystem>
               <boIdClientSystemLabel>BRUYES_1</boIdClientSystemLabel>
               <deliveryNumber>BRUYES_1</deliveryNumber>
               <deliveryType>F8</deliveryType>
               <items>
                <interactionControls>
                <usecase>
                  <usecaseId>EC_APPROVAL_DATA</usecaseId>
                </usecase>
                <ids>
                  <boIdClientSystem>id_1</boIdClientSystem>
                  <clientSystemId>ERP_1</clientSystemId>
                  <boItemIdClientSystem>ITM_1</boItemIdClientSystem>
                </ids>
              </interactionControls>  
                 <itemNumber>1</itemNumber>
                  <idClientSystem>1</idClientSystem>
                  <itemDescription>best food</itemDescription>
                  <prefOriginCountry>DE</prefOriginCountry>
                  <originCountry>DE</originCountry>
                  <originRegion>01</originRegion>
                  <orderNumber>BUREYS_1</orderNumber>
                  <orderItemNumber>1</orderItemNumber>
                  <invoiceIdClientSystem>BRUYES_1</invoiceIdClientSystem>
                  <goodsDescriptions>
                     <language>DE</language>
                     <description>Cool food</description>
                  </goodsDescriptions>
                  <parties>
                     <companyNumber>1650</companyNumber>
                     <country>DE</country>
                     <city>Stuttgart</city>
                     <cityPostBox>71088</cityPostBox>
                     <county></county>
                     <district></district>
                     <fax></fax>
                     <phone></phone>
                     <email></email>
                     <name1>Henderson INc</name1>
                     <name2></name2>
                     <name3></name3>
                     <name4></name4>
                     <postCode></postCode>
                     <postCodePostBox></postCodePostBox>
                     <postBox></postBox>
                     <type>SH</type>
                     <street></street>
                     <street2></street2>
                     <contact>
                        <type></type>
                        <forename></forename>
                        <surname></surname>
                        <email></email>
                        <phone></phone>
                        <initials></initials>
                     </contact>
                  </parties>
                  <costs>
                     <type>PPR0</type>
                     <value>10</value>
                     <currency>EUR</currency>
                  </costs>
                  <quantities>
                     <type>BillingQuantity</type>
                     <unit>ST</unit>
                     <value>10</value>
                  </quantities>
                  <classifications>
                     <type>ECCN</type>
                     <classificationValue>1232132</classificationValue>
                  </classifications>
                  <additionalFields>
                     <type>Type</type>
                     <value>VALUe</value>
                  </additionalFields>
                  <materialNo>M-11</materialNo>
               </items>
                <parties>
                     <companyNumber>1650</companyNumber>
                     <country>DE</country>
                     <city>Stuttgart</city>
                     <cityPostBox>71088</cityPostBox>
                     <county></county>
                     <district></district>
                     <fax></fax>
                     <phone></phone>
                     <email></email>
                     <name1>Henderson INc</name1>
                     <name2></name2>
                     <name3></name3>
                     <name4></name4>
                     <postCode></postCode>
                     <postCodePostBox></postCodePostBox>
                     <postBox></postBox>
                     <type>SH</type>
                     <street></street>
                     <street2></street2>
                     <contact>
                        <type></type>
                        <forename></forename>
                        <surname></surname>
                        <email></email>
                        <phone></phone>
                        <initials></initials>
                     </contact>
                  </parties>
              <parties>
                     <companyNumber>JAM_TEST1</companyNumber>
                     <country>DE</country>
                     <city>Stuttgart</city>
                     <cityPostBox>71088</cityPostBox>
                     <county></county>
                     <district></district>
                     <fax></fax>
                     <phone></phone>
                     <email></email>
                 
                     <name2></name2>
                     <name3></name3>
                     <name4></name4>
                     <postCode></postCode>
                     <postCodePostBox></postCodePostBox>
                     <postBox></postBox>
                     <type>SH</type>
                     <street></street>
                     <street2></street2>
                  </parties>
               <persons>
                  <type>CONTACT</type>
                  <forename>jochey</forename>
                  <surname>Dum</surname>
                  <email></email>
                  <phone></phone>
                  <initials></initials>
               </persons>
               <costs>
                  <type>PPR0</type>
                  <value>10</value>
                  <currency>EUR</currency>
               </costs>
               <quantities>
                  <type>BillingQuantity</type>
                  <unit>ST</unit>
                  <value>1</value>
               </quantities>
               <handlingUnits>
                  <boIdClientSystem>1</boIdClientSystem>
                  <referenceNoHandlingUnit>1</referenceNoHandlingUnit>
                  <typeCode>PKG</typeCode>
                  <typeUNECECode>PKG</typeUNECECode>
                  <referenceSourceObject>1</referenceSourceObject>
                  <handlingUnitNumberFrom>1</handlingUnitNumberFrom>
                  <handlingUnitNumberTo></handlingUnitNumberTo>
                  <contentDescription>ALL</contentDescription>
                  <dimensionHeight>1</dimensionHeight>
                  <dimensionWidth>1</dimensionWidth>
                  <dimensionLength>1</dimensionLength>
                  <dimensionQuantityUnit>cm</dimensionQuantityUnit>
                  <quantities>
                     <type>QUANT_TYPE</type>
                     <unit>ST</unit>
                     <value>1</value>
                  </quantities>
                  <packedItems>
                     <itemIdClientSystem>1</itemIdClientSystem>
                     <quantity>1</quantity>
                  </packedItems>
                  <packedHandlingUnits/>
                  <additionalFields>
                     <type>TYPE</type>
                     <value>VALUE</value>
                  </additionalFields>
               </handlingUnits>
                <additionalFields>
                     <type>TYPE</type>
                     <value>VALUE</value>
                  </additionalFields>
               <transportMeans>
                  <type>BRUYES</type>
                  <identification>ID</identification>
                  <nationality>DE</nationality>
                  <code>CDE</code>
                  <transportModeCode>ModeCode</transportModeCode>
               </transportMeans>
               <deliveryDate>
                  <dateInTimezone>2026-01-01 10:00:00</dateInTimezone>
                  <timezone>UTC</timezone>
               </deliveryDate>
               <shippingDate>
                  <dateInTimezone>2026-01-01 10:00:00</dateInTimezone>
                  <timezone>UTC</timezone>
               </shippingDate>
               <incotermIdentCode></incotermIdentCode>
               <incotermDescription></incotermDescription>
               <incotermDestination></incotermDestination>
               <invoices>
                  <invoiceNumber>1</invoiceNumber>
                  <boIdClientSystem>1</boIdClientSystem>
                  <boIdClientSystemLabel>1</boIdClientSystemLabel>    

                  <invoiceDate>
                     <dateInTimezone>2026-01-01 10:00:00</dateInTimezone>
                     <timezone>UTC</timezone>
                  </invoiceDate>
               </invoices>
            </delivery>
            <mappingProfile>BRUYES</mappingProfile>
         </request>
      </urn:updateDelivery>
   </soapenv:Body>
</soapenv:Envelope>
```

The response of the request above could look like this.  It provides information if the AEB delivery has been created or updated in the field "wasCreated".

```json
{
  "hasErrors": false,
  "hasOnlyRetryableErrors": false,
  "hasWarnings": false,
  "messages": [],
  "wasCreated": true
}
```
```xml
<?xml version="1.0" encoding="UTF-8"?>
<S:Envelope xmlns:S="http://schemas.xmlsoap.org/soap/envelope/">
    <S:Body>
        <ns2:updateDeliveryResponse xmlns:ns2="urn:de.aeb.xnsg.bsm.core.bf.delivery">
            <result>
                <hasErrors>false</hasErrors>
                <hasOnlyRetryableErrors>false</hasOnlyRetryableErrors>
                <hasWarnings>false</hasWarnings>
                <wasCreated>true</wasCreated>
            </result>
        </ns2:updateDeliveryResponse>
    </S:Body>
</S:Envelope>
```

If there was an error, the response could look like this:

```json
{
  "hasErrors": true,
  "hasOnlyRetryableErrors": false,
  "hasWarnings": false,
  "messages": [
    {
      "messageType": "ERROR",
      "messageIdentCode": "EMPTY_MANDATORY_FIELD",
      "messageTexts": [
        {
          "languageISOCode": "en",
          "text": "Use case ID \"CCO_SHP_CUSTOMS_UPD1\" is unknown."
        }
      ],
      "indentationLevel": 0
    }
  ]
}
```
```xml
<?xml version="1.0" encoding="UTF-8"?>
<S:Envelope xmlns:S="http://schemas.xmlsoap.org/soap/envelope/">
    <S:Body>
        <ns2:updateDeliveryResponse xmlns:ns2="urn:de.aeb.xnsg.bsm.core.bf.delivery">
            <result>
                <hasErrors>true</hasErrors>
                <hasOnlyRetryableErrors>false</hasOnlyRetryableErrors>
                <hasWarnings>false</hasWarnings>
                <messages>
                    <messageType>ERROR</messageType>
                    <messageIdentCode>EMPTY_MANDATORY_FIELD</messageIdentCode>
                    <messageTexts>
                        <languageISOCode>de</languageISOCode>
                        <text>Use case ID "CCO_SHP_CUSTOMS_UPD1" is unknown.</text>
                    </messageTexts>
                    <indentationLevel>0</indentationLevel>
                </messages>
            </result>
        </ns2:updateDeliveryResponse>
    </S:Body>
</S:Envelope>
```

### Mapping to a customs declaration

To check the mapping of an AEB delivery to a consignment of Customs Management, look here: [https://docs.aeb.com/doc/cm-3ZxLOQ6TSH/t-3ZxLOQ6TSH](https://docs.aeb.com/doc/cm-NtUocTToRG/t-NtUocTToRG)

<br />

<br />
