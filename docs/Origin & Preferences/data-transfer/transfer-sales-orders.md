---
title: Transfer sales orders
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
