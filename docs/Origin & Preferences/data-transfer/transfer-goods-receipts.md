---
title: Transfer goods receipts
deprecated: false
hidden: false
metadata:
  robots: index
next:
  description: >-
    Now that you transferred all your business objects. You can go on with
    getting data back.
  pages:
    - slug: get-material-master-data-limits
      title: Get material master data (limits)
      type: basic
---
<br />

In the following you can see an API-Call of transfer goods receipts with one goods receipt.

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
        [transferGoodsReceipts](https://rz3.aeb.de/test2bsm/swagger/#/O%26P/transferGoodsReceipts)
      </td>
    </tr>

    <tr>
      <td>
        SOAP
      </td>

      <td>
        [Origin&PreferencesBF (WSDL)](https://rz3.aeb.de/test2bsm/servlet/bf/OriginAndPreferencesBF?WSDL)
        [transferGoodsReceipts (Java Doc)](https://rz3.aeb.de/test2bsm/servlet/bf/doc/OriginAndPreferencesBF/de/aeb/xnsg/onpintegration/bf/onp/IOriginAndPreferencesBF.html#transferGoodsReceipts\(de.aeb.xnsg.onpintegration.bf.onp.TransferGoodsReceiptsRequestDTO\))
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
  "goodsReceiptRequests": [
    {
      "idHost": "2008_4711",
      "labelHost": "2008_4711",
      "organizationalUnit": "1000",
      "referenceNo": "4711",
      "isDeleted": false,
      "goodsReceiptNo": "4711",
      "goodsReceiptDate": "2020-10-10",
      "documentType": "i",
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
          "purchaseOrderNo": "66687",
          "supplierNo": "1200",
          "supplierNoInternal": "1200",
          "value": 100,
          "currency": "EUR",
          "lotSize": 1,
          "quantityUnit": "ST",
          "valueForSubcontracting": 100,
          "movementType": "0001",
          "specialStockIndicator": "1"
        }
      ],
      "deliveryNo": "873621",
      "deliveryDate": "2029-11-10",
      "invoiceNo": "6098760",
      "invoiceDate": "2029-11-10",
      "customerNoForSubcontracting": "1650"
    }
  ]
}
```
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:de.aeb.xnsg.onpintegration.bf.onp">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:transferGoodsReceipts>
         <request>
            <clientIdentCode>AEB_TEST_CLIENT</clientIdentCode>
                <clientSystemId>ERP_SYSTEM_X</clientSystemId>
                <resultLanguageIsoCodes>EN</resultLanguageIsoCodes>
                <userName>ANTON</userName>
            <goodsReceiptRequests>
               <idHost>4711</idHost>
               <labelHost>4711</labelHost>
               <organizationalUnit>DEFAULT</organizationalUnit>
               <referenceNo>4711</referenceNo>
               <isDeleted>false</isDeleted>
               <goodsReceiptNo>4711</goodsReceiptNo>
               <goodsReceiptDate>2024-10-01</goodsReceiptDate>
               <documentType>i</documentType>
               <items>
                  <itemIdHost>1</itemIdHost>
                  <itemLabelHost>1</itemLabelHost>
                  <itemReferenceNo>1</itemReferenceNo>
                  <isDeleted>false</isDeleted>
                  <materialNo>M-11</materialNo>
                  <materialNoInternal>M-11</materialNoInternal>
                  <supplierMaterialNo>1000</supplierMaterialNo>
                  <itemNo>1</itemNo>
                  <purchaseOrderNo>565</purchaseOrderNo>
                  <supplierNo>1000</supplierNo>
                  <supplierNoInternal>000010000</supplierNoInternal>
                  <value>1</value>
                  <currency>EUR</currency>
                  <lotSize>1</lotSize>
                  <quantityUnit>ST</quantityUnit>
               </items>
               <deliveryNo>123</deliveryNo>
               <invoiceNo>123</invoiceNo>
            </goodsReceiptRequests>
         </request>
      </urn:transferGoodsReceipts>
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
      "idHost": "2008_4711"
    }
  ]
}
```
```xml
<?xml version="1.0" encoding="UTF-8"?>
<S:Envelope xmlns:S="http://schemas.xmlsoap.org/soap/envelope/">
    <S:Body>
        <ns2:transferGoodsReceiptsResponse xmlns:ns2="urn:de.aeb.xnsg.onpintegration.bf.onp">
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
        </ns2:transferGoodsReceiptsResponse>
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
        <ns2:transferGoodsReceiptsResponse xmlns:ns2="urn:de.aeb.xnsg.onpintegration.bf.onp">
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
        </ns2:transferGoodsReceiptsResponse>
    </S:Body>
</S:Envelope>
```
