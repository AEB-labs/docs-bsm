---
title: Transfer purchase orders
deprecated: false
hidden: false
metadata:
  robots: index
next:
  description: Go on with goods receipt.
  pages:
    - slug: transfer-goods-receipts
      title: Transfer goods receipts
      type: basic
---
<br />

In the following you can see an API-Call of transfer purchase orders with one purchase order.

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
        <Anchor label="transferPurchaseOrders" target="_blank" href="https://rz3.aeb.de/test2bsm/swagger/#/O%26P/transferPurchaseOrders">transferPurchaseOrders</Anchor>
      </td>
    </tr>

    <tr>
      <td>
        SOAP
      </td>

      <td>
        <Anchor label="Origin&PreferencesBF (WSDL)" target="_blank" href="https://rz3.aeb.de/test2bsm/servlet/bf/OriginAndPreferencesBF?WSDL">Origin&PreferencesBF (WSDL)</Anchor>
        <Anchor label="transferPurchaseOrders (Java Doc)" target="_blank" href="https://rz3.aeb.de/test2bsm/servlet/bf/doc/OriginAndPreferencesBF/de/aeb/xnsg/onpintegration/bf/onp/IOriginAndPreferencesBF.html#transferPurchaseOrders(de.aeb.xnsg.onpintegration.bf.onp.TransferPurchaseOrdersRequestDTO)">transferPurchaseOrders (Java Doc)</Anchor>
      </td>
    </tr>
  </tbody>
</Table>

```json
{
  "clientSystemId": "TEST_ID",
  "clientIdentCode": "API_TEST",
  "userName": "API_TEST",
  "resultLanguageIsoCodes": [
    "en"
  ],
  "purchaseOrderRequests": [
    {
      "idHost": "4711",
      "labelHost": "4711",
      "organizationalUnit": "1000",
      "referenceNo": "4711",
      "isDeleted": false,
      "purchaseOrderNo": "4711",
      "purchaseOrderDate": "2010-10-10",
      "items": [
        {
          "itemIdHost": "1",
          "itemLabelHost": "1",
          "itemReferenceNo": "1",
          "isDeleted": false,
          "materialNo": "M-11",
          "materialNoInternal": "M-11",
          "supplierMaterialNo": "M-15",
          "itemNo": "1",
          "supplierNo": "1200",
          "value": 100,
          "currency": "EUR",
          "lotSize": 1,
          "quantityUnit": "ST",
          "isSupplierMaterial": true,
          "comment": "This is a comment"
        }
      ],
      "supplierNo": "1200",
      "supplierNoInternal": "1200"
    }
  ]
}

```
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:de.aeb.xnsg.onpintegration.bf.onp">
    <soapenv:Header/>
    <soapenv:Body>
        <urn:transferPurchaseOrders>
            <request>
                <clientIdentCode>AEB_TEST_CLIENT</clientIdentCode>
                <clientSystemId>ERP_SYSTEM_X</clientSystemId>
                <resultLanguageIsoCodes>EN</resultLanguageIsoCodes>
                <userName>Steve</userName>
                <purchaseOrderRequests>
                    <idHost>1</idHost>
                    <labelHost>1</labelHost>
                    <organizationalUnit>DEFAULT</organizationalUnit>
                    <referenceNo>1</referenceNo>
                    <isDeleted>false</isDeleted>
                    <purchaseOrderNo>1</purchaseOrderNo>
                    <purchaseOrderDate>2024-10-10</purchaseOrderDate>
                    <items>
                        <itemIdHost>1</itemIdHost>
                        <itemLabelHost>1</itemLabelHost>
                        <itemReferenceNo>1</itemReferenceNo>
                        <isDeleted>false</isDeleted>
                        <materialNo>M-11</materialNo>
                        <materialNoInternal>M-11</materialNoInternal>
                        <supplierMaterialNo></supplierMaterialNo>
                        <itemNo>1</itemNo>
                        <supplierNo>1000</supplierNo>
                        <value>1</value>
                        <currency>EUR</currency>
                        <lotSize>1</lotSize>
                        <quantityUnit>ST</quantityUnit>
                        <isSupplierMaterial>false</isSupplierMaterial>
                        <comment>asdsadsa</comment>
                    </items>
                    <supplierNo>1000</supplierNo>
                    <supplierNoInternal>00000010000</supplierNoInternal>
                </purchaseOrderRequests>
            </request>
        </urn:transferPurchaseOrders>
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
        <ns2:transferPurchaseOrdersResponse xmlns:ns2="urn:de.aeb.xnsg.onpintegration.bf.onp">
            <result>
                <hasErrors>false</hasErrors>
                <hasOnlyRetryableErrors>false</hasOnlyRetryableErrors>
                <hasWarnings>false</hasWarnings>
                <responses>
                    <hasErrors>false</hasErrors>
                    <hasWarnings>false</hasWarnings>
                    <idHost>1</idHost>
                </responses>
            </result>
        </ns2:transferPurchaseOrdersResponse>
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
        <ns2:transferPurchaseOrdersResponse xmlns:ns2="urn:de.aeb.xnsg.onpintegration.bf.onp">
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
        </ns2:transferPurchaseOrdersResponse>
    </S:Body>
</S:Envelope>
```
