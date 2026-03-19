---
title: Transfer bill of materials
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
        <urn:transferBillOfMaterials>
            <request>
                <clientIdentCode>{{client}}</clientIdentCode>
                <clientSystemId>ERP_SYSTEM_1</clientSystemId>
                <resultLanguageIsoCodes>EN</resultLanguageIsoCodes>
                <userName>{{user}}</userName>
                <billOfMaterialRequests>
                    <idHost>id_123</idHost>
                    <labelHost>Id 123</labelHost>
                    <organizationalUnit>DE_1000</organizationalUnit>
                    <referenceNo>123</referenceNo>
                    <isDeleted>false</isDeleted>
                    <materialNo>123</materialNo>
                    <materialNoInternal>00000123</materialNoInternal>
                    <orderItemReference></orderItemReference>
                    <description>car</description>
                    <createDate>2026-10-02</createDate>
                    <modifyDate>2026-10-02</modifyDate>
                    <validToDate>2029-10-02</validToDate>
                    <quantity>1</quantity>
                    <quantityUnit>ST</quantityUnit>
                    <value>100</value>
                    <manufactoringCosts>200</manufactoringCosts>
                    <currency>EUR</currency>
                    <lotSize>1</lotSize>
                    <isHandledMinimal>true</isHandledMinimal>
                    <isMaterialSet>false</isMaterialSet>
                    <isActive>true</isActive>
                    <alternativeNo>5000</alternativeNo>
                    <productOrigin>DE</productOrigin>
                    <items>
                        <itemIdHost>1</itemIdHost>
                        <itemLabelHost>1</itemLabelHost>
                        <itemReferenceNo>1</itemReferenceNo>
                        <isDeleted>false</isDeleted>
                        <materialNo>M-11</materialNo>
                        <materialNoInternal>M-11</materialNoInternal>
                        <materialOrderItemReference></materialOrderItemReference>
                        <type>X</type>
                        <description>Other one</description>
                        <quantity>1</quantity>
                        <quantityUnit>ST</quantityUnit>
                        <value>100</value>
                        <lotSize>1</lotSize>
                    </items>
                </billOfMaterialRequests>
            </request>
        </urn:transferBillOfMaterials>
    </soapenv:Body>
</soapenv:Envelope>
```

And here you can see the response of the request.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<S:Envelope xmlns:S="http://schemas.xmlsoap.org/soap/envelope/">
    <S:Body>
        <ns2:transferAddressesResponse xmlns:ns2="urn:de.aeb.xnsg.onpintegration.bf.onp">
            <result>
                <hasErrors>false</hasErrors>
                <hasOnlyRetryableErrors>false</hasOnlyRetryableErrors>
                <hasWarnings>false</hasWarnings>
                <responses>
                    <hasErrors>false</hasErrors>
                    <hasWarnings>false</hasWarnings>
                    <idHost>su_0000001004</idHost>
                </responses>
            </result>
        </ns2:transferAddressesResponse>
    </S:Body>
</S:Envelope>
```

In case of an error it looks like this.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<S:Envelope xmlns:S="http://schemas.xmlsoap.org/soap/envelope/">
    <S:Body>
        <ns2:transferAddressesResponse xmlns:ns2="urn:de.aeb.xnsg.onpintegration.bf.onp">
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
        </ns2:transferAddressesResponse>
    </S:Body>
</S:Envelope>
```
