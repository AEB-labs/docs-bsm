---
title: 'Determine freight costs for existing shipping orders  '
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
        <Anchor label="getShipment" target="_blank" href="https://rz3.aeb.de/test2bsm/swagger/#/BSM%20Carrier/getShipment">getShipment</Anchor>
      </td>
    </tr>

    <tr>
      <td>
        SOAP
      </td>

      <td>
        <Anchor label="BSMCarrierBF (WSDL)" target="_blank" href="https://rz3.aeb.de/test2bsm/servlet/bf/BSMCarrierBF?WSDL">BSMCarrierBF (WSDL)</Anchor>
        <Anchor label="getShipment (Java Doc)" target="_blank" href="https://rz3.aeb.de/test2bsm/servlet/bf/doc/BSMCarrierBF/de/aeb/xnsg/bsm/carrier/bf/IBSMCarrierBF.html#getShipment(de.aeb.xnsg.bsm.carrier.bf.get.GetShipmentRequestDTO)">getShipment (Java Doc)</Anchor>
      </td>
    </tr>
  </tbody>
</Table>

The API expects the following parameters:

* Reference - references for an existing shipping order in Carrier Connect. See  <Anchor label="ShpimentReferenceDTO" target="_blank" href="https://rz3.aeb.de/test1bsm/servlet/bf/doc/DLCarrierBF/de/aeb/xnsg/dl/bf/DLShipmentReferenceDTO.html">ShpimentReferenceDTO</Anchor>
* IncludeDocuments - indicates that documents should be returned - boolean (TRUE or FALSE)
* ShippingTime  - the expected time of shipping, in format HH:MM:SS

Here is an example call with reference the shipping order by transactionId:

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

If the request could determine the costs the response could look like this:

```json
{
  "hasErrors": false,
  "hasOnlyRetryableErrors": false,
  "hasWarnings": false,
  "messages": [],
  "shipment": {
    "quotedData": {
      "netPrice": {
        "value": 43.34,
        "currencyIso": "EUR"
      },
      "priceItemsDescription": "code: RatedShipment\n  code: TotalCharges amount: 43.34 currency: EUR\n  code: TransportationCharges amount: 43.34 currency: EUR\n  code: BaseServiceCharge amount: 40.99 currency: EUR\n  code: ServiceOptionsCharges amount: 0.00 currency: EUR\n  code: ItemizedCharges\n    code: 573 amount: 2.35 currency: EUR\n",
      "transitDate": "2026-06-04",
      "transitTime": "23:30:00",
      "messages": [
        {
          "code": "110971",
          "text": "Your invoice may vary from the displayed reference rates"
        },
        {
          "code": "112259",
          "text": "International Processing Fee has been added to the Shipment."
        },
        {
          "code": "120900",
          "text": "User Id and Shipper Number combination is not qualified to receive negotiated rates"
        }
      ]
    },
    "shipment": {
      "hasWarnings": false,
      "syncId": "-1",
      "transactionId": "PR1     400008000026920251105101712JLO  1000",
      "organizationUnitClientSystem": "TEST",
      "shipmentNumber": "0000078",
      "revisionNumber": 0,
      "referenceNumber1": "80000269",
      "boStatus": {
        "identCode": "RDYFORCOMPLETE",
        "descriptions": [
          {
            "languageISOCode": "en",
            "text": "Ready to print labels"
          }
        ]
      },
      "isCompleted": false,
      "carrierNames": [
        {
          "languageISOCode": "en",
          "text": "UPS EMEA"
        }
      ],
      "carrierIdentCode": "UPS",
      "carrierServiceNames": [
        {
          "languageISOCode": "en",
          "text": "UPS Expedited"
        }
      ],
      "carrierServiceCode": "UPS_EXPE",
      "freightCosts": {
        "value": 0,
        "currencyIso": "EUR"
      },
      "shippingDate": "2026-05-29",
      "shippingPt": {
        "companyNumber": "1010",
        "name": "Shipping Point 1010 DE",
        "street": "Sigmaringerstr. 109",
        "postcode": "70567",
        "city": "Stuttgart",
        "countryISOCode": "DE",
        "county": "BW",
        "emailAddress": "noreply@sap.com"
      },
      "consignee": {
        "companyNumber": "1650",
        "name": "Henderson Inc.",
        "street": "12 Lincoln Ave",
        "postcode": "60696",
        "city": "Chicago",
        "countryISOCode": "US",
        "county": "IL"
      },
      "consigneeContact": {
        "name": "asdf",
        "phone": "1234"
      },
      "termsOfDeliveryCode": "FCA",
      "incotermDestination": "Hamburg",
      "securityStatus": "NOTSPECIFIED",
      "payerOfChargRole": "SHIPPER",
      "payerOfDutRole": "SHIPPER",
      "contents": "Wichtig",
      "goodsValue": {
        "value": 114,
        "currencyIso": "EUR"
      },
      "customsValue": {
        "value": 114,
        "currencyIso": "EUR"
      },
      "insuranceValue": {
        "value": 114,
        "currencyIso": "EUR"
      },
      "codValue": {
        "value": 114,
        "currencyIso": "EUR"
      },
      "isDocumentShipment": false,
      "shipmentTotals": {},
      "accountInfo": {},
      "additionalValues": {
        "fields": [
          {
            "name": "UPSMRN",
            "type": "string"
          },
          {
            "name": "UPSINSURCHAR",
            "type": "decimal"
          },
          {
            "name": "UPSFREICHAR",
            "type": "decimal"
          },
          {
            "name": "UPSOTHERCHAR",
            "type": "decimal"
          },
          {
            "name": "UPSDISCOUNT",
            "type": "decimal"
          }
        ]
      },
      "packages": [
        {
          "packageNumber": 1,
          "referenceNumber1": "1",
          "packageTypeIdentCode": "CI",
          "contents": "Wichtig",
          "dimensions": {
            "length": 10,
            "width": 10,
            "height": 10,
            "identCode": "CM"
          },
          "grossWeight": {
            "value": 1,
            "unit": "KG"
          },
          "boStatus": {
            "identCode": "READY",
            "descriptions": [
              {
                "languageISOCode": "en",
                "text": "Complete"
              }
            ]
          },
          "additionalValues": {},
          "hazardousGoodsData": {
            "hazardousGoodsType": "NONE"
          },
          "freightClass": "NONE"
        }
      ],
      "items": [
        {
          "itemNumber": 1,
          "itemTransactionId": "0080000269_000010",
          "referenceNumber1": "10",
          "boStatus": {
            "identCode": "READY",
            "descriptions": [
              {
                "languageISOCode": "en",
                "text": "Complete"
              }
            ]
          },
          "customsTariffNumber": "84185011900",
          "description": "Monitor 35",
          "countryOfOriginsISOCode": "RU",
          "quantity": {
            "value": 1,
            "unit": "ST"
          },
          "netWeight": {
            "value": 16.2,
            "unit": "KG"
          },
          "grossWeight": {
            "value": 18,
            "unit": "KG"
          },
          "despatchProcedureIdentCode": "NONE",
          "despatchProcedureNames": [
            {
              "languageISOCode": "en",
              "text": "None"
            }
          ],
          "additionalValues": {}
        }
      ],
      "isHazardousGoodsShipment": false,
      "isContainingSpecialSubstances": false
    }
  }
}
```
```xml
<?xml version="1.0" encoding="UTF-8"?>
<S:Envelope xmlns:S="http://schemas.xmlsoap.org/soap/envelope/">
    <S:Body>
        <ns2:getShipmentResponse xmlns:ns2="urn:de.aeb.xnsg.bsm.carrier.bf">
            <result>
                <hasErrors>false</hasErrors>
                <hasOnlyRetryableErrors>false</hasOnlyRetryableErrors>
                <hasWarnings>false</hasWarnings>
                <shipment>
                    <quotedData>
                        <netPrice>
                            <value>43.34</value>
                            <currencyIso>EUR</currencyIso>
                        </netPrice>
                        <priceItemsDescription>code: RatedShipment
  code: TotalCharges amount: 43.34 currency: EUR
  code: TransportationCharges amount: 43.34 currency: EUR
  code: BaseServiceCharge amount: 40.99 currency: EUR
  code: ServiceOptionsCharges amount: 0.00 currency: EUR
  code: ItemizedCharges
    code: 573 amount: 2.35 currency: EUR</priceItemsDescription>
                        <transitDate>2026-06-04</transitDate>
                        <transitTime>23:30:00</transitTime>
                        <messages>
                            <code>110971</code>
                            <text>Your invoice may vary from the displayed reference rates</text>
                        </messages>
                        <messages>
                            <code>112259</code>
                            <text>International Processing Fee has been added to the Shipment.</text>
                        </messages>
                        <messages>
                            <code>120900</code>
                            <text>User Id and Shipper Number combination is not qualified to receive negotiated rates</text>
                        </messages>
                    </quotedData>
                    <shipment>
                        <hasWarnings>false</hasWarnings>
                        <syncId>4280116</syncId>
                        <transactionId>PR1     400008000026920251105101712JLO  1000</transactionId>
                        <organizationUnitClientSystem>TEST</organizationUnitClientSystem>
                        <shipmentNumber>0000078</shipmentNumber>
                        <revisionNumber>0</revisionNumber>
                        <referenceNumber1>80000269</referenceNumber1>
                        <boStatus>
                            <identCode>RDYFORCOMPLETE</identCode>
                            <descriptions>
                                <languageISOCode>en</languageISOCode>
                                <text>Ready to print labels</text>
                            </descriptions>
                        </boStatus>
                        <isCompleted>false</isCompleted>
                        <carrierNames>
                            <languageISOCode>en</languageISOCode>
                            <text>UPS EMEA</text>
                        </carrierNames>
                        <carrierIdentCode>UPS</carrierIdentCode>
                        <carrierServiceNames>
                            <languageISOCode>en</languageISOCode>
                            <text>UPS Expedited</text>
                        </carrierServiceNames>
                        <carrierServiceCode>UPS_EXPE</carrierServiceCode>
                        <freightCosts>
                            <value>0.00</value>
                            <currencyIso>EUR</currencyIso>
                        </freightCosts>
                        <shippingDate>2026-05-29</shippingDate>
                        <shippingPt>
                            <companyNumber>1010</companyNumber>
                            <name>Shipping Point 1010 DE</name>
                            <street>Sigmaringerstr. 109</street>
                            <postcode>70567</postcode>
                            <city>Stuttgart</city>
                            <countryISOCode>DE</countryISOCode>
                            <county>BW</county>
                            <emailAddress>noreply@sap.com</emailAddress>
                        </shippingPt>
                        <consignee>
                            <companyNumber>1650</companyNumber>
                            <name>Henderson Inc.</name>
                            <street>12 Lincoln Ave</street>
                            <postcode>60696</postcode>
                            <city>Chicago</city>
                            <countryISOCode>US</countryISOCode>
                            <county>IL</county>
                        </consignee>
                        <consigneeContact>
                            <name>asdf</name>
                            <phone>1234</phone>
                        </consigneeContact>
                        <termsOfDeliveryCode>FCA</termsOfDeliveryCode>
                        <incotermDestination>Hamburg</incotermDestination>
                        <securityStatus>NOTSPECIFIED</securityStatus>
                        <payerOfChargRole>SHIPPER</payerOfChargRole>
                        <payerOfDutRole>SHIPPER</payerOfDutRole>
                        <contents>Wichtig</contents>
                        <goodsValue>
                            <value>114.00</value>
                            <currencyIso>EUR</currencyIso>
                        </goodsValue>
                        <customsValue>
                            <value>114.00</value>
                            <currencyIso>EUR</currencyIso>
                        </customsValue>
                        <insuranceValue>
                            <value>114.00</value>
                            <currencyIso>EUR</currencyIso>
                        </insuranceValue>
                        <codValue>
                            <value>114.00</value>
                            <currencyIso>EUR</currencyIso>
                        </codValue>
                        <isDocumentShipment>false</isDocumentShipment>
                        <shipmentTotals/>
                        <accountInfo/>
                        <additionalValues>
                            <fields>
                                <name>UPSMRN</name>
                                <type>string</type>
                            </fields>
                            <fields>
                                <name>UPSINSURCHAR</name>
                                <type>decimal</type>
                            </fields>
                            <fields>
                                <name>UPSFREICHAR</name>
                                <type>decimal</type>
                            </fields>
                            <fields>
                                <name>UPSOTHERCHAR</name>
                                <type>decimal</type>
                            </fields>
                            <fields>
                                <name>UPSDISCOUNT</name>
                                <type>decimal</type>
                            </fields>
                        </additionalValues>
                        <packages>
                            <packageNumber>1</packageNumber>
                            <referenceNumber1>1</referenceNumber1>
                            <packageTypeIdentCode>CI</packageTypeIdentCode>
                            <contents>Wichtig</contents>
                            <dimensions>
                                <length>10.00</length>
                                <width>10.00</width>
                                <height>10.00</height>
                                <identCode>CM</identCode>
                            </dimensions>
                            <grossWeight>
                                <value>1.000</value>
                                <unit>KG</unit>
                            </grossWeight>
                            <boStatus>
                                <identCode>READY</identCode>
                                <descriptions>
                                    <languageISOCode>en</languageISOCode>
                                    <text>Complete</text>
                                </descriptions>
                            </boStatus>
                            <additionalValues/>
                            <hazardousGoodsData>
                                <hazardousGoodsType>NONE</hazardousGoodsType>
                            </hazardousGoodsData>
                            <freightClass>NONE</freightClass>
                        </packages>
                        <items>
                            <itemNumber>1</itemNumber>
                            <itemTransactionId>0080000269_000010</itemTransactionId>
                            <referenceNumber1>10</referenceNumber1>
                            <boStatus>
                                <identCode>READY</identCode>
                                <descriptions>
                                    <languageISOCode>en</languageISOCode>
                                    <text>Complete</text>
                                </descriptions>
                            </boStatus>
                            <customsTariffNumber>84185011900</customsTariffNumber>
                            <description>Monitor 35</description>
                            <countryOfOriginsISOCode>RU</countryOfOriginsISOCode>
                            <quantity>
                                <value>1.000</value>
                                <unit>ST</unit>
                            </quantity>
                            <netWeight>
                                <value>16.200</value>
                                <unit>KG</unit>
                            </netWeight>
                            <grossWeight>
                                <value>18.000</value>
                                <unit>KG</unit>
                            </grossWeight>
                            <despatchProcedureIdentCode>NONE</despatchProcedureIdentCode>
                            <despatchProcedureNames>
                                <languageISOCode>en</languageISOCode>
                                <text>None</text>
                            </despatchProcedureNames>
                            <additionalValues/>
                        </items>
                        <isHazardousGoodsShipment>false</isHazardousGoodsShipment>
                        <isContainingSpecialSubstances>false</isContainingSpecialSubstances>
                    </shipment>
                </shipment>
            </result>
        </ns2:getShipmentResponse>
    </S:Body>
</S:Envelope>
```

In case there was an error the response could look like this.

```json
{
  "hasErrors": true,
  "hasOnlyRetryableErrors": false,
  "hasWarnings": false,
  "messages": [
    {
      "messageType": "ERROR",
      "messageIdentCode": "INVALID_VALUE",
      "messageTexts": [
        {
          "languageISOCode": "en",
          "text": "An error has occurred when calling the service Quotes API.\r\nMessage: Invalid timestamp format. Use timestamps according to ISO-8601. The date component must be in the format: yyyy-MM-dd; the time component must be in the format: HH:mm:ss using a 24 hour clock.The date and time parts are separated by the letter T (e.g. 2024-07-31T17:00:00)\r\nField: collectionDateTime\r\nCode: INVALID_VALUE\r\nValue: 2026-05-29T12:00:00ksdjfsf\r\nAPI path: /quotes"
        }
      ],
      "indentationLevel": 0
    }
  ],
  "shipment": {
    "shipment": {
      "hasWarnings": false,
      "syncId": "4280116",
      "transactionId": "PR1     400008000026920251105101712JLO  1000",
      "organizationUnitClientSystem": "TEST",
      "shipmentNumber": "0000078",
      "revisionNumber": 0,
      "referenceNumber1": "80000269",
      "boStatus": {
        "identCode": "RDYFORCOMPLETE",
        "descriptions": [
          {
            "languageISOCode": "en",
            "text": "Ready to print labels"
          }
        ]
      },
      "isCompleted": false,
      "carrierNames": [
        {
          "languageISOCode": "en",
          "text": "UPS EMEA"
        }
      ],
      "carrierIdentCode": "UPS",
      "carrierServiceNames": [
        {
          "languageISOCode": "en",
          "text": "UPS Expedited"
        }
      ],
      "carrierServiceCode": "UPS_EXPE",
      "freightCosts": {
        "value": 0,
        "currencyIso": "EUR"
      },
      "shippingDate": "2026-05-29",
      "shippingPt": {
        "companyNumber": "1010",
        "name": "Shipping Point 1010 DE",
        "street": "Sigmaringerstr. 109",
        "postcode": "70567",
        "city": "Stuttgart",
        "countryISOCode": "DE",
        "county": "BW",
        "emailAddress": "noreply@sap.com"
      },
      "consignee": {
        "companyNumber": "1650",
        "name": "Henderson Inc.",
        "street": "12 Lincoln Ave",
        "postcode": "60696",
        "city": "Chicago",
        "countryISOCode": "US",
        "county": "IL"
      },
      "consigneeContact": {
        "name": "asdf",
        "phone": "1234"
      },
      "termsOfDeliveryCode": "FCA",
      "incotermDestination": "Hamburg",
      "securityStatus": "NOTSPECIFIED",
      "payerOfChargRole": "SHIPPER",
      "payerOfDutRole": "SHIPPER",
      "contents": "Wichtig",
      "goodsValue": {
        "value": 114,
        "currencyIso": "EUR"
      },
      "customsValue": {
        "value": 114,
        "currencyIso": "EUR"
      },
      "insuranceValue": {
        "value": 114,
        "currencyIso": "EUR"
      },
      "codValue": {
        "value": 114,
        "currencyIso": "EUR"
      },
      "isDocumentShipment": false,
      "shipmentTotals": {},
      "accountInfo": {},
      "additionalValues": {
        "fields": [
          {
            "name": "UPSMRN",
            "type": "string"
          },
          {
            "name": "UPSINSURCHAR",
            "type": "decimal"
          },
          {
            "name": "UPSFREICHAR",
            "type": "decimal"
          },
          {
            "name": "UPSOTHERCHAR",
            "type": "decimal"
          },
          {
            "name": "UPSDISCOUNT",
            "type": "decimal"
          }
        ]
      },
      "packages": [
        {
          "packageNumber": 1,
          "referenceNumber1": "1",
          "packageTypeIdentCode": "CI",
          "contents": "Wichtig",
          "dimensions": {
            "length": 10,
            "width": 10,
            "height": 10,
            "identCode": "CM"
          },
          "grossWeight": {
            "value": 1,
            "unit": "KG"
          },
          "boStatus": {
            "identCode": "READY",
            "descriptions": [
              {
                "languageISOCode": "en",
                "text": "Complete"
              }
            ]
          },
          "additionalValues": {},
          "hazardousGoodsData": {
            "hazardousGoodsType": "NONE"
          },
          "freightClass": "NONE"
        }
      ],
      "items": [
        {
          "itemNumber": 1,
          "itemTransactionId": "0080000269_000010",
          "referenceNumber1": "10",
          "boStatus": {
            "identCode": "READY",
            "descriptions": [
              {
                "languageISOCode": "en",
                "text": "Complete"
              }
            ]
          },
          "customsTariffNumber": "84185011900",
          "description": "Monitor 35",
          "countryOfOriginsISOCode": "RU",
          "quantity": {
            "value": 1,
            "unit": "ST"
          },
          "netWeight": {
            "value": 16.2,
            "unit": "KG"
          },
          "grossWeight": {
            "value": 18,
            "unit": "KG"
          },
          "despatchProcedureIdentCode": "NONE",
          "despatchProcedureNames": [
            {
              "languageISOCode": "en",
              "text": "None"
            }
          ],
          "additionalValues": {}
        }
      ],
      "isHazardousGoodsShipment": false,
      "isContainingSpecialSubstances": false
    }
  }
}
```
```xml
<?xml version="1.0" encoding="UTF-8"?>
<S:Envelope xmlns:S="http://schemas.xmlsoap.org/soap/envelope/">
    <S:Body>
        <ns2:getShipmentResponse xmlns:ns2="urn:de.aeb.xnsg.bsm.carrier.bf">
            <result>
                <hasErrors>true</hasErrors>
                <hasOnlyRetryableErrors>false</hasOnlyRetryableErrors>
                <hasWarnings>false</hasWarnings>
                <messages>
                    <messageType>ERROR</messageType>
                    <messageIdentCode>INVALID_VALUE</messageIdentCode>
                    <messageTexts>
                        <languageISOCode>en</languageISOCode>
                        <text>An error has occurred when calling the service Quotes API.&#13;
Message: Invalid timestamp format. Use timestamps according to ISO-8601. The date component must be in the format: yyyy-MM-dd; the time component must be in the format: HH:mm:ss using a 24 hour clock.The date and time parts are separated by the letter T (e.g. 2024-07-31T17:00:00)&#13;
Field: collectionDateTime&#13;
Code: INVALID_VALUE&#13;
Value: 2026-05-29T12:00:00dsjkfk&#13;
API path: /quotes</text>
                    </messageTexts>
                    <indentationLevel>0</indentationLevel>
                </messages>
                <shipment>
                    <shipment>
                        <hasWarnings>false</hasWarnings>
                        <syncId>4280116</syncId>
                        <transactionId>PR1     400008000026920251105101712JLO  1000</transactionId>
                        <organizationUnitClientSystem>TEST</organizationUnitClientSystem>
                        <shipmentNumber>0000078</shipmentNumber>
                        <revisionNumber>0</revisionNumber>
                        <referenceNumber1>80000269</referenceNumber1>
                        <boStatus>
                            <identCode>RDYFORCOMPLETE</identCode>
                            <descriptions>
                                <languageISOCode>en</languageISOCode>
                                <text>Ready to print labels</text>
                            </descriptions>
                        </boStatus>
                        <isCompleted>false</isCompleted>
                        <carrierNames>
                            <languageISOCode>en</languageISOCode>
                            <text>UPS EMEA</text>
                        </carrierNames>
                        <carrierIdentCode>UPS</carrierIdentCode>
                        <carrierServiceNames>
                            <languageISOCode>en</languageISOCode>
                            <text>UPS Expedited</text>
                        </carrierServiceNames>
                        <carrierServiceCode>UPS_EXPE</carrierServiceCode>
                        <freightCosts>
                            <value>0.00</value>
                            <currencyIso>EUR</currencyIso>
                        </freightCosts>
                        <shippingDate>2026-05-29</shippingDate>
                        <shippingPt>
                            <companyNumber>1010</companyNumber>
                            <name>Shipping Point 1010 DE</name>
                            <street>Sigmaringerstr. 109</street>
                            <postcode>70567</postcode>
                            <city>Stuttgart</city>
                            <countryISOCode>DE</countryISOCode>
                            <county>BW</county>
                            <emailAddress>noreply@sap.com</emailAddress>
                        </shippingPt>
                        <consignee>
                            <companyNumber>1650</companyNumber>
                            <name>Henderson Inc.</name>
                            <street>12 Lincoln Ave</street>
                            <postcode>60696</postcode>
                            <city>Chicago</city>
                            <countryISOCode>US</countryISOCode>
                            <county>IL</county>
                        </consignee>
                        <consigneeContact>
                            <name>asdf</name>
                            <phone>1234</phone>
                        </consigneeContact>
                        <termsOfDeliveryCode>FCA</termsOfDeliveryCode>
                        <incotermDestination>Hamburg</incotermDestination>
                        <securityStatus>NOTSPECIFIED</securityStatus>
                        <payerOfChargRole>SHIPPER</payerOfChargRole>
                        <payerOfDutRole>SHIPPER</payerOfDutRole>
                        <contents>Wichtig</contents>
                        <goodsValue>
                            <value>114.00</value>
                            <currencyIso>EUR</currencyIso>
                        </goodsValue>
                        <customsValue>
                            <value>114.00</value>
                            <currencyIso>EUR</currencyIso>
                        </customsValue>
                        <insuranceValue>
                            <value>114.00</value>
                            <currencyIso>EUR</currencyIso>
                        </insuranceValue>
                        <codValue>
                            <value>114.00</value>
                            <currencyIso>EUR</currencyIso>
                        </codValue>
                        <isDocumentShipment>false</isDocumentShipment>
                        <shipmentTotals/>
                        <accountInfo/>
                        <additionalValues>
                            <fields>
                                <name>UPSMRN</name>
                                <type>string</type>
                            </fields>
                            <fields>
                                <name>UPSINSURCHAR</name>
                                <type>decimal</type>
                            </fields>
                            <fields>
                                <name>UPSFREICHAR</name>
                                <type>decimal</type>
                            </fields>
                            <fields>
                                <name>UPSOTHERCHAR</name>
                                <type>decimal</type>
                            </fields>
                            <fields>
                                <name>UPSDISCOUNT</name>
                                <type>decimal</type>
                            </fields>
                        </additionalValues>
                        <packages>
                            <packageNumber>1</packageNumber>
                            <referenceNumber1>1</referenceNumber1>
                            <packageTypeIdentCode>CI</packageTypeIdentCode>
                            <contents>Wichtig</contents>
                            <dimensions>
                                <length>10.00</length>
                                <width>10.00</width>
                                <height>10.00</height>
                                <identCode>CM</identCode>
                            </dimensions>
                            <grossWeight>
                                <value>1.000</value>
                                <unit>KG</unit>
                            </grossWeight>
                            <boStatus>
                                <identCode>READY</identCode>
                                <descriptions>
                                    <languageISOCode>en</languageISOCode>
                                    <text>Complete</text>
                                </descriptions>
                            </boStatus>
                            <additionalValues/>
                            <hazardousGoodsData>
                                <hazardousGoodsType>NONE</hazardousGoodsType>
                            </hazardousGoodsData>
                            <freightClass>NONE</freightClass>
                        </packages>
                        <items>
                            <itemNumber>1</itemNumber>
                            <itemTransactionId>0080000269_000010</itemTransactionId>
                            <referenceNumber1>10</referenceNumber1>
                            <boStatus>
                                <identCode>READY</identCode>
                                <descriptions>
                                    <languageISOCode>en</languageISOCode>
                                    <text>Complete</text>
                                </descriptions>
                            </boStatus>
                            <customsTariffNumber>84185011900</customsTariffNumber>
                            <description>Monitor 35</description>
                            <countryOfOriginsISOCode>RU</countryOfOriginsISOCode>
                            <quantity>
                                <value>1.000</value>
                                <unit>ST</unit>
                            </quantity>
                            <netWeight>
                                <value>16.200</value>
                                <unit>KG</unit>
                            </netWeight>
                            <grossWeight>
                                <value>18.000</value>
                                <unit>KG</unit>
                            </grossWeight>
                            <despatchProcedureIdentCode>NONE</despatchProcedureIdentCode>
                            <despatchProcedureNames>
                                <languageISOCode>en</languageISOCode>
                                <text>None</text>
                            </despatchProcedureNames>
                            <additionalValues/>
                        </items>
                        <isHazardousGoodsShipment>false</isHazardousGoodsShipment>
                        <isContainingSpecialSubstances>false</isContainingSpecialSubstances>
                    </shipment>
                </shipment>
            </result>
        </ns2:getShipmentResponse>
    </S:Body>
</S:Envelope>
```

<br />

<br />

<br />