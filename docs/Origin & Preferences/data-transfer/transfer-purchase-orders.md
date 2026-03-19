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

In the following you can see an API-Call of transfer Addresses with one address.

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