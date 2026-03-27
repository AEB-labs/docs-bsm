---
title: 'Request quotes '
deprecated: false
hidden: false
metadata:
  robots: index
---
## getQuotes API

The getQuotes API allows you to determine the available shipping options of the selected transport service provider at an early, freely selectable stage in the process. Based on he provided shipping order data, you will receive:

* the possible services of the transport service provider,
* the respective prices, and
* the associated schedule.

Unlike the getShipment API, this call does not require an existing shipping order in Carrier Connect. However, if packages are not yet physically packed at this point, the data basis (e.g. planned weights and dimensions) on which the freight costs are to be determined must be specified within the call.

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
        <Anchor label="getQuotes" target="_blank" href="https://rz3.aeb.de/test2bsm/swagger/#/BSM%20Carrier/getQuotes">getQuotes</Anchor>
      </td>
    </tr>

    <tr>
      <td>
        SOAP
      </td>

      <td>
        <Anchor label="BSMCarrierBF (WSDL)" target="_blank" href="https://rz3.aeb.de/test2bsm/servlet/bf/BSMCarrierBF?WSDL">BSMCarrierBF (WSDL)</Anchor> |
        <Anchor label="getQuotes (Java Doc)" target="_blank" href="https://rz3.aeb.de/test2bsm/servlet/bf/doc/BSMCarrierBF/de/aeb/xnsg/bsm/carrier/bf/IBSMCarrierBF.html#getQuotes(de.aeb.xnsg.bsm.carrier.bf.get.GetQuotesRequestDTO)">getQuotes (Java Doc)</Anchor>
      </td>
    </tr>
  </tbody>
</Table>

The API expects two parameters in the request:

* Shipment -  shipping data to request a quote, see list of fields [here](https://rz3.aeb.de/test1bsm/servlet/bf/doc/DLCarrierBF/de/aeb/xnsg/dl/bf/DLShipmentRequestDataDTO.html)
* ShippingTime  - the expected time of shipping, in format HH:MM:SS

Example call:

```json
{
  "clientSystemId": "PR1_400",
  "clientIdentCode": "{{client}}",
  "userName": "{{user}}",
  "resultLanguageIsoCodes": [
    "en"
  ],
  "shipment": {
    "transactionId": "123",
    "transactionLabel": "123",
    "organizationUnitClientSystem": "1000",
    "masterShipmentTransactionId": "",
    "isDocumentShipment": false,
    "templateName": "",
    "referenceNumber1": "123",
    "referenceNumber2": "",
    "numberOfExchangePallets": 0,
    "shipToServicePointID": "",
    "shipFromServicePointID": "",
    "remark": "A remark",
    "shippingDate": "2026-11-14",
    "contents": "Content",
    "extCarrierShipNum": "",
    "extCarrierShipNumBasic": "",
    "extCarrierShipNumReturn": "",
    "extCarrierShipNumBasicReturn": "",
    "shippingPt": {
      "companyNumber": "1010",
      "name": "AEB Zentrale",
      "street": "Sigmaringer Straße 5",
      "postcode": "88459",
      "city": "Stuttgart",
      "countryISOCode": "DE"
    },
    "customsValue": {
      "value": 100,
      "currencyIso": "EUR"
    },
    "consignee": {
      "companyNumber": "1650",
      "name": "Henderson INC",
      "street": "Hafenstrasse 678",
      "postcode": "54001",
      "city": "Hamburg",
      "district": "string",
      "countryISOCode": "DE"
    },
    "carrierIdentCode": "UPS",
    "serviceCode": null,
    "termsOfDeliveryCode": "FCA",
    "codValue": {
      "value": 100,
      "currencyIso": "EUR"
    },
    "insuranceValue": {
      "value": 100,
      "currencyIso": "EUR"
    },
    "goodsValue": {
      "value": 100,
      "currencyIso": "EUR"
    },
    "invoiceValue": {
      "value": 100,
      "currencyIso": "EUR"
    },
    "loadingMeters": 0,
    "palletPlaces": 0,
    "packages": [
      {
        "packageTypeIdentCode": "CT",
        "packageTransactionId": "0000000642",
        "referenceNumber1": "300001500",
        "extCarrierPackNum": "string",
        "grossWeight": {
          "value": 1.000,
          "unit": "kg"
        },
        "dimensions": {
          "length": 10,
          "width": 10,
          "height": 10,
          "identCode": "CM"
        },
        "containedItems": [
          {
            "packedItemTransactionId": "string",
            "shipmentReference": {
              "transactionId": "string",
              "referenceNumber1": "string",
              "shipmentNumber": "string"
            },
            "itemTransactionId": "string",
            "referenceNumber1": "string",
            "quantityValue": 0
          }
        ],
        "hazardousGoodsData": {
          "hazardousGoodsType": "string",
          "packagingTypeHandling": "string",
          "hazardQValue": 0
        },
        "transportEquipment": {
          "identification": "string",
          "equipmentTransactionId": "string"
        },
        "marks": "string",
        "stackability": "string",
        "freightClass": "string",
        "nmfcCode": "string",
        "nmfcSubCode": "string",
        "loadingMeters": 0,
        "palletPlaces": 0
      }
    ],
    "items": [
      {
        "itemNumber": 10,
        "itemTransactionId": "10",
        "referenceNumber1": "10",
        "customsTariffNumber": "81022941",
        "description": "LCD Monitor",
        "countryOfOriginsISOCode": "DE",
        "quantity": {
          "value": 1,
          "unit": "kg"
        },
        "netWeight": {
          "value": 1,
          "unit": "kg"
        },
        "grossWeight": {
          "value": 1,
          "unit": "kg"
        },
        "customsValue": {
          "value": 1000,
          "currencyIso": "EUR"
        },
        "goodsValue": {
          "value": 100,
          "currencyIso": "EUR"
        }
      }
    ]    
  },
  "shippingTime": "12:00:00"
}
```
```xml XML
<SHIPMENT>
        <CARRIERIDENTCODE>UPS</CARRIERIDENTCODE>
        <CONSIGNEE>
          <INITFROMCOMPANYMASTERFILEDATA>false</INITFROMCOMPANYMASTERFILEDATA>
          <COMPANYNUMBER>1200</COMPANYNUMBER>
          <CITY>Hamburg</CITY>
          <COUNTRYISOCODE>DE</COUNTRYISOCODE>
          <EMAILADDRESS>info@acme.com</EMAILADDRESS>
          <NAME>Elblogistik Services</NAME>
          <POSTCODE>54001</POSTCODE>
          <STREET>Hafenstrasse 678</STREET>
        </CONSIGNEE>
        <CONTENTS>Electronic parts</CONTENTS>
        <INCOTERMDESTINATION>Stuttgart</INCOTERMDESTINATION>
        <INVOICEVALUE>
          <CURRENCYISO>EUR</CURRENCYISO>
          <VALUE>2222.00</VALUE>
        </INVOICEVALUE>
        <ISDOCUMENTSHIPMENT>false</ISDOCUMENTSHIPMENT>
        <ITEMS>
          <COUNTRYOFORIGINSISOCODE>DE</COUNTRYOFORIGINSISOCODE>
          <CUSTOMSTARIFFNUMBER>81022941</CUSTOMSTARIFFNUMBER>
          <CUSTOMSVALUE>
            <CURRENCYISO>EUR</CURRENCYISO>
            <VALUE>2222.00</VALUE>
          </CUSTOMSVALUE>
          <DESCRIPTION>LCD Monitor</DESCRIPTION>
          <GOODSVALUE>
            <CURRENCYISO>EUR</CURRENCYISO>
            <VALUE>2222.00</VALUE>
          </GOODSVALUE>
          <ITEMTRANSACTIONID>0080000584_000010</ITEMTRANSACTIONID>
          <NETWEIGHT>
            <UNIT>KG</UNIT>
            <VALUE>16.200</VALUE>
          </NETWEIGHT>
          <GROSSWEIGHT>
            <UNIT>KG</UNIT>
            <VALUE>18.000</VALUE>
          </GROSSWEIGHT>
          <QUANTITY>
            <UNIT>ST</UNIT>
            <VALUE>1.000</VALUE>
          </QUANTITY>
          <REFERENCENUMBER1>10</REFERENCENUMBER1>
        </ITEMS>
        <PACKAGES>
          <CONTAINEDITEMS>
            <ITEMTRANSACTIONID>0080000584_000010</ITEMTRANSACTIONID>
            <QUANTITYVALUE>1.000</QUANTITYVALUE>
          </CONTAINEDITEMS>
          <DIMENSIONS>
            <IDENTCODE>CM</IDENTCODE>
            <HEIGHT>100.00</HEIGHT>
            <LENGTH>60.00</LENGTH>
            <WIDTH>30.00</WIDTH>
          </DIMENSIONS>
          <GROSSWEIGHT>
            <UNIT>KG</UNIT>
            <VALUE>25.000</VALUE>
          </GROSSWEIGHT>
          <PACKAGETYPEIDENTCODE>CT</PACKAGETYPEIDENTCODE>
          <REFERENCENUMBER1>300001500</REFERENCENUMBER1>
          <PACKAGETRANSACTIONID>0000000642</PACKAGETRANSACTIONID>
        </PACKAGES>
        <REFERENCENUMBER1>80000584</REFERENCENUMBER1>
        <SHIPPINGDATE>2026-02-16</SHIPPINGDATE>
        <SHIPPINGPT>
          <COMPANYNUMBER>1010</COMPANYNUMBER>
          <CITY>Stuttgart</CITY>
          <COUNTRYISOCODE>DE</COUNTRYISOCODE>
          <COUNTY>BW</COUNTY>
          <EMAILADDRESS>info@shipper.com</EMAILADDRESS>
          <NAME>Shipping Point 1010 DE</NAME>
          <POSTCODE>70567</POSTCODE>
          <STREET>Sigmaringerstr. 109</STREET>
        </SHIPPINGPT>
        <TERMSOFDELIVERYCODE>FCA</TERMSOFDELIVERYCODE>
        <TRANSACTIONID>S01     400008000058420260216092737JLF  1010</TRANSACTIONID>
        <TRANSACTIONLABEL>80000584</TRANSACTIONLABEL>
        <ORGANIZATIONUNITCLIENTSYSTEM>7000</ORGANIZATIONUNITCLIENTSYSTEM>        
</SHIPMENT>
<SHIPPINGTIME>18:30:00</SHIPPINGTIME>      
```

If Everything is fine the response of the request could look like this.

```java
{
  "hasErrors": false,
  "hasOnlyRetryableErrors": false,
  "hasWarnings": false,
  "messages": [],
  "quotedServices": [
    {
      "originalServiceCode": "07",
      "aebServiceCode": "UPS_EXPR",
      "data": {
        "netPrice": {
          "value": 27.34,
          "currencyIso": "EUR"
        },
        "priceItemsDescription": "code: RatedShipment\n  code: TotalCharges amount: 27.34 currency: EUR\n  code: TransportationCharges amount: 27.34 currency: EUR\n  code: BaseServiceCharge amount: 27.34 currency: EUR\n  code: ServiceOptionsCharges amount: 0.00 currency: EUR\n",
        "messages": [
          {
            "code": "110971",
            "text": "Your invoice may vary from the displayed reference rates"
          },
          {
            "code": "111598",
            "text": "Time in Transit information unavailable."
          },
          {
            "code": "120900",
            "text": "User Id and Shipper Number combination is not qualified to receive negotiated rates"
          }
        ]
      }
    },
    {
      "originalServiceCode": "11",
      "aebServiceCode": "UPS_STD_SHP",
      "data": {
        "netPrice": {
          "value": 5.16,
          "currencyIso": "EUR"
        },
        "priceItemsDescription": "code: RatedShipment\n  code: TotalCharges amount: 5.16 currency: EUR\n  code: TransportationCharges amount: 5.16 currency: EUR\n  code: BaseServiceCharge amount: 5.16 currency: EUR\n  code: ServiceOptionsCharges amount: 0.00 currency: EUR\n  code: ItemizedCharges\n    code: 406 amount: 0.00 currency: EUR\n",
        "messages": [
          {
            "code": "110971",
            "text": "Your invoice may vary from the displayed reference rates"
          },
          {
            "code": "111598",
            "text": "Time in Transit information unavailable."
          },
          {
            "code": "120900",
            "text": "User Id and Shipper Number combination is not qualified to receive negotiated rates"
          }
        ]
      }
    },
    {
      "originalServiceCode": "54",
      "aebServiceCode": "UPS_EXPR_PLUS",
      "data": {
        "netPrice": {
          "value": 47.05,
          "currencyIso": "EUR"
        },
        "priceItemsDescription": "code: RatedShipment\n  code: TotalCharges amount: 47.05 currency: EUR\n  code: TransportationCharges amount: 47.05 currency: EUR\n  code: BaseServiceCharge amount: 47.05 currency: EUR\n  code: ServiceOptionsCharges amount: 0.00 currency: EUR\n",
        "messages": [
          {
            "code": "110971",
            "text": "Your invoice may vary from the displayed reference rates"
          },
          {
            "code": "111598",
            "text": "Time in Transit information unavailable."
          },
          {
            "code": "120900",
            "text": "User Id and Shipper Number combination is not qualified to receive negotiated rates"
          }
        ]
      }
    },
    {
      "originalServiceCode": "65",
      "aebServiceCode": "UPS_EXPR_SAV",
      "data": {
        "netPrice": {
          "value": 13.67,
          "currencyIso": "EUR"
        },
        "priceItemsDescription": "code: RatedShipment\n  code: TotalCharges amount: 13.67 currency: EUR\n  code: TransportationCharges amount: 13.67 currency: EUR\n  code: BaseServiceCharge amount: 13.67 currency: EUR\n  code: ServiceOptionsCharges amount: 0.00 currency: EUR\n",
        "messages": [
          {
            "code": "110971",
            "text": "Your invoice may vary from the displayed reference rates"
          },
          {
            "code": "111598",
            "text": "Time in Transit information unavailable."
          },
          {
            "code": "120900",
            "text": "User Id and Shipper Number combination is not qualified to receive negotiated rates"
          }
        ]
      }
    },
    {
      "originalServiceCode": "74",
      "aebServiceCode": "UPS_EXPR_1200",
      "data": {
        "netPrice": {
          "value": 21.04,
          "currencyIso": "EUR"
        },
        "priceItemsDescription": "code: RatedShipment\n  code: TotalCharges amount: 21.04 currency: EUR\n  code: TransportationCharges amount: 21.04 currency: EUR\n  code: BaseServiceCharge amount: 21.04 currency: EUR\n  code: ServiceOptionsCharges amount: 0.00 currency: EUR\n",
        "messages": [
          {
            "code": "110971",
            "text": "Your invoice may vary from the displayed reference rates"
          },
          {
            "code": "111598",
            "text": "Time in Transit information unavailable."
          },
          {
            "code": "120900",
            "text": "User Id and Shipper Number combination is not qualified to receive negotiated rates"
          }
        ]
      }
    }
  ]
}
```
```xml
<?xml version="1.0" encoding="UTF-8"?>
<S:Envelope xmlns:S="http://schemas.xmlsoap.org/soap/envelope/">
    <S:Body>
        <ns2:getQuotesResponse xmlns:ns2="urn:de.aeb.xnsg.bsm.carrier.bf">
            <result>
                <hasErrors>false</hasErrors>
                <hasOnlyRetryableErrors>false</hasOnlyRetryableErrors>
                <hasWarnings>false</hasWarnings>
                <quotedServices>
                    <originalServiceCode>54</originalServiceCode>
                    <aebServiceCode>UPS_EXPR_PLUS</aebServiceCode>
                    <originalServiceName>UPS Express Plus</originalServiceName>
                    <data>
                        <netPrice>
                            <value>68.06</value>
                            <currencyIso>EUR</currencyIso>
                        </netPrice>
                        <priceItemsDescription>code: RatedShipment
  code: TotalCharges amount: 68.06 currency: EUR
  code: TransportationCharges amount: 68.06 currency: EUR
  code: BaseServiceCharge amount: 68.06 currency: EUR
  code: ServiceOptionsCharges amount: 0.00 currency: EUR</priceItemsDescription>
                        <transitDate>2026-09-15</transitDate>
                        <transitTime>09:00:00</transitTime>
                        <messages>
                            <code>110971</code>
                            <text>Your invoice may vary from the displayed reference rates</text>
                        </messages>
                        <messages>
                            <code>120900</code>
                            <text>User Id and Shipper Number combination is not qualified to receive negotiated rates</text>
                        </messages>
                    </data>
                </quotedServices>
                <quotedServices>
                    <originalServiceCode>07</originalServiceCode>
                    <aebServiceCode>UPS_EXPR</aebServiceCode>
                    <originalServiceName>UPS Express</originalServiceName>
                    <data>
                        <netPrice>
                            <value>36.17</value>
                            <currencyIso>EUR</currencyIso>
                        </netPrice>
                        <priceItemsDescription>code: RatedShipment
  code: TotalCharges amount: 36.17 currency: EUR
  code: TransportationCharges amount: 36.17 currency: EUR
  code: BaseServiceCharge amount: 36.17 currency: EUR
  code: ServiceOptionsCharges amount: 0.00 currency: EUR</priceItemsDescription>
                        <transitDate>2026-09-15</transitDate>
                        <transitTime>10:30:00</transitTime>
                        <messages>
                            <code>110971</code>
                            <text>Your invoice may vary from the displayed reference rates</text>
                        </messages>
                        <messages>
                            <code>120900</code>
                            <text>User Id and Shipper Number combination is not qualified to receive negotiated rates</text>
                        </messages>
                    </data>
                </quotedServices>
                <quotedServices>
                    <originalServiceCode>74</originalServiceCode>
                    <aebServiceCode>UPS_EXPR_1200</aebServiceCode>
                    <originalServiceName>UPS Express 12:00</originalServiceName>
                    <data>
                        <netPrice>
                            <value>30.70</value>
                            <currencyIso>EUR</currencyIso>
                        </netPrice>
                        <priceItemsDescription>code: RatedShipment
  code: TotalCharges amount: 30.70 currency: EUR
  code: TransportationCharges amount: 30.70 currency: EUR
  code: BaseServiceCharge amount: 30.70 currency: EUR
  code: ServiceOptionsCharges amount: 0.00 currency: EUR</priceItemsDescription>
                        <transitDate>2026-09-15</transitDate>
                        <transitTime>12:00:00</transitTime>
                        <messages>
                            <code>110971</code>
                            <text>Your invoice may vary from the displayed reference rates</text>
                        </messages>
                        <messages>
                            <code>120900</code>
                            <text>User Id and Shipper Number combination is not qualified to receive negotiated rates</text>
                        </messages>
                    </data>
                </quotedServices>
                <quotedServices>
                    <originalServiceCode>65</originalServiceCode>
                    <aebServiceCode>UPS_EXPR_SAV</aebServiceCode>
                    <originalServiceName>UPS Express Saver</originalServiceName>
                    <data>
                        <netPrice>
                            <value>22.49</value>
                            <currencyIso>EUR</currencyIso>
                        </netPrice>
                        <priceItemsDescription>code: RatedShipment
  code: TotalCharges amount: 22.49 currency: EUR
  code: TransportationCharges amount: 22.49 currency: EUR
  code: BaseServiceCharge amount: 22.49 currency: EUR
  code: ServiceOptionsCharges amount: 0.00 currency: EUR</priceItemsDescription>
                        <transitDate>2026-09-15</transitDate>
                        <transitTime>23:30:00</transitTime>
                        <messages>
                            <code>110971</code>
                            <text>Your invoice may vary from the displayed reference rates</text>
                        </messages>
                        <messages>
                            <code>120900</code>
                            <text>User Id and Shipper Number combination is not qualified to receive negotiated rates</text>
                        </messages>
                    </data>
                </quotedServices>
                <quotedServices>
                    <originalServiceCode>11</originalServiceCode>
                    <aebServiceCode>UPS_STD_SHP</aebServiceCode>
                    <originalServiceName>UPS Standard</originalServiceName>
                    <data>
                        <netPrice>
                            <value>9.47</value>
                            <currencyIso>EUR</currencyIso>
                        </netPrice>
                        <priceItemsDescription>code: RatedShipment
  code: TotalCharges amount: 9.47 currency: EUR
  code: TransportationCharges amount: 9.47 currency: EUR
  code: BaseServiceCharge amount: 9.47 currency: EUR
  code: ServiceOptionsCharges amount: 0.00 currency: EUR
  code: ItemizedCharges
    code: 406 amount: 0.00 currency: EUR</priceItemsDescription>
                        <transitDate>2026-09-15</transitDate>
                        <transitTime>23:30:00</transitTime>
                        <messages>
                            <code>110971</code>
                            <text>Your invoice may vary from the displayed reference rates</text>
                        </messages>
                        <messages>
                            <code>120900</code>
                            <text>User Id and Shipper Number combination is not qualified to receive negotiated rates</text>
                        </messages>
                    </data>
                </quotedServices>
            </result>
        </ns2:getQuotesResponse>
    </S:Body>
</S:Envelope>
```

If there is an error it could look like this.

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
          "text": "An error has occurred when calling the service Quotes API.\r\nMessage: Invalid timestamp format. Use timestamps according to ISO-8601. The date component must be in the format: yyyy-MM-dd; the time component must be in the format: HH:mm:ss using a 24 hour clock.The date and time parts are separated by the letter T (e.g. 2024-07-31T17:00:00)\r\nField: collectionDateTime\r\nCode: INVALID_VALUE\r\nValue: 2026-11-14aT12:00:00\r\nAPI path: /quotes"
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
        <ns2:getQuotesResponse xmlns:ns2="urn:de.aeb.xnsg.bsm.carrier.bf">
            <result>
                <hasErrors>true</hasErrors>
                <hasOnlyRetryableErrors>false</hasOnlyRetryableErrors>
                <hasWarnings>false</hasWarnings>
                <messages>
                    <messageType>ERROR</messageType>
                    <messageIdentCode>INVALID_VALUE</messageIdentCode>
                    <messageTexts>
                        <languageISOCode>de</languageISOCode>
                        <text>Es ist ein Fehler beim Aufruf des Services Quotes API aufgetreten. &#13;
Meldung: Invalid timestamp format. Use timestamps according to ISO-8601. The date component must be in the format: yyyy-MM-dd; the time component must be in the format: HH:mm:ss using a 24 hour clock.The date and time parts are separated by the letter T (e.g. 2024-07-31T17:00:00)&#13;
Feld: collectionDateTime&#13;
Code: INVALID_VALUE&#13;
Wert: 2asT13:33:00&#13;
API-Pfad: /quotes</text>
                    </messageTexts>
                    <indentationLevel>0</indentationLevel>
                </messages>
            </result>
        </ns2:getQuotesResponse>
    </S:Body>
</S:Envelope>
```

<br />

<br />
