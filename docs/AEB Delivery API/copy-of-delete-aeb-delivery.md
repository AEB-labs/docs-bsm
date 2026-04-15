---
title: Get an AEB Delivery
deprecated: false
hidden: false
metadata:
  robots: index
---
Sometime it might be needed to get the AEB Delivery via API.

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
        <Anchor label="getAEBDelivery" target="_blank" href="https://rz3.aeb.de/test2bsm/swagger/#/AEB%20Delivery/getDelivery">getAEBDelivery</Anchor>
      </td>
    </tr>

    <tr>
      <td>
        SOAP
      </td>

      <td>
        <Anchor label="AEBDeliveryBF (WSDL)" target="_blank" href="https://rz3.aeb.de/test2bsm/servlet/bf/AEBDeliveryBF?WSDL">AEBDeliveryBF (WSDL)</Anchor> |
        <Anchor label="getAEBDelivery (Java Doc)" target="_blank" href="https://rz3.aeb.de/test2bsm/servlet/bf/doc/AEBDeliveryBF/de/aeb/xnsg/bsm/core/bf/delivery/IAEBDeliveryBF.html#getDelivery(de.aeb.xnsg.bsm.core.bf.delivery.get.GetAEBDeliveryRequestDTO)">getAEBDelivery (Java Doc)</Anchor>
      </td>
    </tr>
  </tbody>
</Table>

The request for a get request has to be like this.

```json
{
  "clientSystemId": "BRUYES",
  "clientIdentCode": "{{client}}",
  "userName": "API_TEST",
  "resultLanguageIsoCodes": [
    "en"
  ],
  "boIdClientSystem": "BRUYES_1"    
}
```
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:de.aeb.xnsg.bsm.core.bf.delivery">
    <soapenv:Header/>
    <soapenv:Body>
        <urn:getDelivery>
            <request>
                <clientSystemId>BRUYES</clientSystemId>
                <clientIdentCode>{{client}}</clientIdentCode>
                <userName>SOMEONE</userName>
                <resultLanguageIsoCodes>DE</resultLanguageIsoCodes>
                <boIdClientSystem>BRUYES_1</boIdClientSystem>               
            </request>
        </urn:getDelivery>
    </soapenv:Body>
</soapenv:Envelope>
```

If an AEB delivery is found the response looks like this.

```json
{
  "hasErrors": false,
  "hasOnlyRetryableErrors": false,
  "hasWarnings": false,
  "messages": [],
  "delivery": {
    "boIdClientSystem": "BRUYES_1",
    "boIdClientSystemLabel": "BRUYES_1",
    "deliveryNumber": "BRUYES_1",
    "deliveryType": "STD_OUTBOUND_DELIVERY",
    "items": [
      {
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
        "parties": [],
        "costs": [],
        "quantities": [],
        "classifications": [],
        "additionalFields": [
          {
            "type": "Type",
            "value": "VALUe"
          }
        ],
        "materialNo": "M-11"
      }
    ],
    "parties": [],
    "persons": [],
    "costs": [],
    "quantities": [],
    "handlingUnits": [
      {
        "boIdClientSystem": "1",
        "referenceNoHandlingUnit": "1",
        "typeCode": "PKG",
        "typeUNECECode": "PKG",
        "referenceSourceObject": "1",
        "handlingUnitNumberFrom": "1",
        "contentDescription": "ALL",
        "dimensionHeight": 1,
        "dimensionWidth": 1,
        "dimensionLength": 1,
        "dimensionQuantityUnit": "cm",
        "quantities": [],
        "packedItems": [
          {
            "itemIdClientSystem": "1",
            "quantity": 1
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
    "transportMeans": [],
    "deliveryDate": {
      "dateInTimezone": "2026-01-01 11:00:00",
      "timezone": "UTC"
    },
    "shippingDate": {
      "dateInTimezone": "2026-01-01 11:00:00",
      "timezone": "UTC"
    },
    "invoices": [
      {
        "invoiceNumber": "1",
        "boIdClientSystem": "1",
        "boIdClientSystemLabel": "1",
        "invoicePrice": {
          "type": "STD_INVOICE_PRICE",
          "value": 100,
          "currency": "EUR"
        },
        "invoiceDate": {
          "dateInTimezone": "2026-01-01 11:00:00",
          "timezone": "UTC"
        }
      }
    ]
  }
}
```
```xml
<?xml version="1.0" encoding="UTF-8"?>
<S:Envelope xmlns:S="http://schemas.xmlsoap.org/soap/envelope/">
    <S:Body>
        <ns2:getDeliveryResponse xmlns:ns2="urn:de.aeb.xnsg.bsm.core.bf.delivery">
            <result>
                <hasErrors>false</hasErrors>
                <hasOnlyRetryableErrors>false</hasOnlyRetryableErrors>
                <hasWarnings>false</hasWarnings>
                <delivery>
                    <boIdClientSystem>BRUYES_1</boIdClientSystem>
                    <boIdClientSystemLabel>BRUYES_1</boIdClientSystemLabel>
                    <deliveryNumber>BRUYES_1</deliveryNumber>
                    <deliveryType>STD_OUTBOUND_DELIVERY</deliveryType>
                    <items>
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
                        <additionalFields>
                            <type>Type</type>
                            <value>VALUe</value>
                        </additionalFields>
                        <materialNo>M-11</materialNo>
                    </items>
                    <handlingUnits>
                        <boIdClientSystem>1</boIdClientSystem>
                        <referenceNoHandlingUnit>1</referenceNoHandlingUnit>
                        <typeCode>PKG</typeCode>
                        <typeUNECECode>PKG</typeUNECECode>
                        <referenceSourceObject>1</referenceSourceObject>
                        <handlingUnitNumberFrom>1</handlingUnitNumberFrom>
                        <contentDescription>ALL</contentDescription>
                        <dimensionHeight>1.000</dimensionHeight>
                        <dimensionWidth>1.000</dimensionWidth>
                        <dimensionLength>1.000</dimensionLength>
                        <dimensionQuantityUnit>cm</dimensionQuantityUnit>
                        <packedItems>
                            <itemIdClientSystem>1</itemIdClientSystem>
                            <quantity>1.000</quantity>
                        </packedItems>
                        <additionalFields>
                            <type>TYPE</type>
                            <value>VALUE</value>
                        </additionalFields>
                    </handlingUnits>
                    <additionalFields>
                        <type>TYPE</type>
                        <value>VALUE</value>
                    </additionalFields>
                    <deliveryDate>
                        <dateInTimezone>2026-01-01 11:00:00</dateInTimezone>
                        <timezone>UTC</timezone>
                    </deliveryDate>
                    <shippingDate>
                        <dateInTimezone>2026-01-01 11:00:00</dateInTimezone>
                        <timezone>UTC</timezone>
                    </shippingDate>
                    <invoices>
                        <invoiceNumber>1</invoiceNumber>
                        <boIdClientSystem>1</boIdClientSystem>
                        <boIdClientSystemLabel>1</boIdClientSystemLabel>
                        <invoicePrice>
                            <type>STD_INVOICE_PRICE</type>
                            <value>100.00</value>
                            <currency>EUR</currency>
                        </invoicePrice>
                        <invoiceDate>
                            <dateInTimezone>2026-01-01 11:00:00</dateInTimezone>
                            <timezone>UTC</timezone>
                        </invoiceDate>
                    </invoices>
                </delivery>
            </result>
        </ns2:getDeliveryResponse>
    </S:Body>
</S:Envelope>
```

If an error occured it looks like this.

```json
{
  "hasErrors": true,
  "hasOnlyRetryableErrors": false,
  "hasWarnings": false,
  "messages": [
    {
      "messageType": "ERROR",
      "messageIdentCode": "INTERNAL_SERVER_ERROR",
      "messageTexts": [
        {
          "languageISOCode": "en",
          "text": "An error occured: ExceptionID:d71d7e86a1f906ca488619b86a975aa7fddbfbfb"
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
        <ns2:getDeliveryResponse xmlns:ns2="urn:de.aeb.xnsg.bsm.core.bf.delivery">
            <result>
                <hasErrors>true</hasErrors>
                <hasOnlyRetryableErrors>false</hasOnlyRetryableErrors>
                <hasWarnings>false</hasWarnings>
                <messages>
                    <messageType>ERROR</messageType>
                    <messageIdentCode>INTERNAL_SERVER_ERROR</messageIdentCode>
                    <messageTexts>
                        <languageISOCode>de</languageISOCode>
                        <text>Es ist ein Fehler aufgetreten: ExceptionID:d71d7e86a1f906ca488619b86a975aa7fddbfbfb</text>
                    </messageTexts>
                    <indentationLevel>0</indentationLevel>
                </messages>
            </result>
        </ns2:getDeliveryResponse>
    </S:Body>
</S:Envelope>
```

<br />