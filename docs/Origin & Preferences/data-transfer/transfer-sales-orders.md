---
title: Transfer sales orders
deprecated: false
hidden: false
metadata:
  robots: index
next:
  description: Go on with purchase orders.
  pages:
    - slug: transfer-purchase-orders
      title: Transfer purchase orders
      type: basic
---
<br />

In the following you can see an API-Call of transfer Addresses with one address.

```json
{
  "clientSystemId": "ERP_SYSTEM_X",
  "clientIdentCode": "API_TEST",
  "userName": "API_TEST",
  "resultLanguageIsoCodes": [
    "en"
  ],
  "salesOrderRequests": [
    {
      "idHost": "4711",
      "labelHost": "4711",
      "organizationalUnit": "1000",
      "referenceNo": "4711",
      "isDeleted": false,
      "salesOrderNo": "4711",
      "salesOrderDate": "2020-12-10",
      "items": [
        {
          "itemIdHost": "1",
          "itemLabelHost": "1",
          "itemReferenceNo": "1",
          "isDeleted": false,
          "materialNo": "M-11",
          "materialNoInternal": "M-11",
          "customerMaterialNo": "M-15",
          "itemNo": "1",
          "value": 100,
          "currency": "EUR",
          "lotSize": 1,
          "quantityUnit": "EUR"
        }
      ],
      "customerNo": "1650",
      "customerNoInternal": "1650"
    }
  ]
}
```
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:de.aeb.xnsg.onpintegration.bf.onp">
    <soapenv:Header/>
    <soapenv:Body>
        <urn:transferSalesOrders>
            <request>
                <clientIdentCode>AEB_TEST_CLIENT</clientIdentCode>
                <clientSystemId>ERP_SYSTEM_X</clientSystemId>
                <resultLanguageIsoCodes>EN</resultLanguageIsoCodes>
                <userName>Tom</userName>
                <salesOrderRequests>
                    <idHost>4711</idHost>
                    <labelHost>4711</labelHost>
                    <organizationalUnit>DEFAULT</organizationalUnit>
                    <referenceNo>4711</referenceNo>
                    <isDeleted>false</isDeleted>
                    <salesOrderNo>4711</salesOrderNo>
                    <salesOrderDate>2010-01-01</salesOrderDate>
                    <items>
                        <itemIdHost>1</itemIdHost>
                        <itemLabelHost>1</itemLabelHost>
                        <itemReferenceNo>1</itemReferenceNo>
                        <isDeleted>false</isDeleted>
                        <materialNo>M-11</materialNo>
                        <materialNoInternal>M-11</materialNoInternal>
                        <materialOrderItemReference></materialOrderItemReference>
                        <customerMaterialNo></customerMaterialNo>
                        <itemNo>1</itemNo>
                        <value>100</value>
                        <currency>EUR</currency>
                        <lotSize>1</lotSize>
                        <quantityUnit>ST</quantityUnit>
                    </items>
                    <customerNo>1650</customerNo>
                    <customerNoInternal>0000001650</customerNoInternal>
                </salesOrderRequests>
            </request>
        </urn:transferSalesOrders>
    </soapenv:Body>
</soapenv:Envelope>
```

And here you can see the response of the request.

```json
{
  "hasErrors": false,
  "hasOnlyRetryableErrors": false,
  "hasWarnings": false,
  "messages": [],
  "responses": [
    {
      "hasErrors": false,
      "hasWarnings": false,
      "messages": [],
      "idHost": "4711"
    }
  ]
}
```
```xml
<?xml version="1.0" encoding="UTF-8"?>
<S:Envelope xmlns:S="http://schemas.xmlsoap.org/soap/envelope/">
    <S:Body>
        <ns2:transferSalesOrdersResponse xmlns:ns2="urn:de.aeb.xnsg.onpintegration.bf.onp">
            <result>
                <hasErrors>false</hasErrors>
                <hasOnlyRetryableErrors>false</hasOnlyRetryableErrors>
                <hasWarnings>false</hasWarnings>
                <responses>
                    <hasErrors>false</hasErrors>
                    <hasWarnings>false</hasWarnings>
                    <idHost>4711</idHost>
                </responses>
            </result>
        </ns2:transferSalesOrdersResponse>
    </S:Body>
</S:Envelope>
```

In case of an error it looks like this.

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
          "text": "The mandatory field \"idHost\" must be filled."
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
        <ns2:transferSalesOrdersResponse xmlns:ns2="urn:de.aeb.xnsg.onpintegration.bf.onp">
            <result>
                <hasErrors>true</hasErrors>
                <hasOnlyRetryableErrors>false</hasOnlyRetryableErrors>
                <hasWarnings>false</hasWarnings>
                <messages>
                    <messageType>ERROR</messageType>
                    <messageIdentCode>EMPTY_MANDATORY_FIELD</messageIdentCode>
                    <messageTexts>
                        <languageISOCode>en</languageISOCode>
                        <text>The mandatory field "idHost" must be filled.</text>
                    </messageTexts>
                    <indentationLevel>0</indentationLevel>
                </messages>
            </result>
        </ns2:transferSalesOrdersResponse>
    </S:Body>
</S:Envelope>
```
