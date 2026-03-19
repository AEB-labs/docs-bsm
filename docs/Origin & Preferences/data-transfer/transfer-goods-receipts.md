---
title: Transfer goods receipts
deprecated: false
hidden: false
metadata:
  robots: index
---
<br />

In the following you can see an API-Call of transfer Addresses with one address.

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
