---
title: Declaration of origin
deprecated: false
hidden: false
metadata:
  robots: index
---
If you like to have a declaration of origin on your invoice document or a check if a transaction has preference you could use our API getDeclarationOfOrigin like the following.

```json
```
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:de.aeb.xnsg.onpintegration.bf.declarationoforigin">
    <soapenv:Header/>
    <soapenv:Body>
        <urn:getDeclarationOfOrigin>
            <request>
                <clientIdentCode>AEB_TEST_CLIENT</clientIdentCode>
                <clientSystemId>ERP_SYSTEM_X</clientSystemId>
                <resultLanguageIsoCodes>DE</resultLanguageIsoCodes>
                <resultLanguageIsoCodes>EN</resultLanguageIsoCodes>
                <userName>{{user}}</userName>
                <destinationCountry>CH</destinationCountry>
                <documentDate>2026-01-27</documentDate>
                <factoryPriceCurrency>EUR</factoryPriceCurrency>
                <idHost>0090000138_U_F5</idHost>
                <place>Stuttgart</place>
                <signatoryName>Emil</signatoryName>
                <isInvoiceSigned>false</isInvoiceSigned>
                <items>
                    <factoryPrice>1111.000</factoryPrice>
                    <itemNo>000010</itemNo>
                    <materialNo>MAT</materialNo>
                    <materialNoInternal>MAT</materialNoInternal>
                    <materialOrderItemReference>4711_10</materialOrderItemReference>
                    <quantity>1.0000000</quantity>
                </items>
                <labelHost>Client: 400 Invoice: 90000138 Sales document category: U Invoice type: F5</labelHost>
                <mainOrganizationalUnit>1010</mainOrganizationalUnit>
                <organizationalUnit>1010</organizationalUnit>
                <referenceNo>90000138</referenceNo>
                <sourceCountry>DE</sourceCountry>
            </request>
        </urn:getDeclarationOfOrigin>
    </soapenv:Body>
</soapenv:Envelope>
```

And the response look like the following.

```json
```
```xml
<?xml version="1.0" encoding="UTF-8"?>
<S:Envelope xmlns:S="http://schemas.xmlsoap.org/soap/envelope/">
    <S:Body>
        <ns2:getDeclarationOfOriginResponse xmlns:ns2="urn:de.aeb.xnsg.onpintegration.bf.declarationoforigin">
            <result>
                <hasErrors>false</hasErrors>
                <hasOnlyRetryableErrors>false</hasOnlyRetryableErrors>
                <hasWarnings>false</hasWarnings>
                <text>The exporter of the products covered by this document declares that, except where otherwise clearly indicated, these products are of EU preferential origin.

Stuttgart, Jan 27, 2026
(Place and date)
________________________________________ Emil
(Signature of the exporter, in addition the name of the person signing the declaration has to be indicated in clear script)</text>
                <isDeclarationOfOriginAllowed>true</isDeclarationOfOriginAllowed>
                <isDeclarationOfOriginToSign>true</isDeclarationOfOriginToSign>
                <items>
                    <itemNo>000010</itemNo>
                    <text>- Preferential origin: EU
- Non-preferential origin: CH</text>
                    <hasPreference>true</hasPreference>
                    <preferentialOrigin>EU</preferentialOrigin>
                </items>
                <linkToDeclOfOriginCheckLog>https://origin-preferences-management-test.internal.aeb.com/doo/home/protocols/doo-sap/view/461?system=0bbcdf2c000ff8c</linkToDeclOfOriginCheckLog>
            </result>
        </ns2:getDeclarationOfOriginResponse>
    </S:Body>
</S:Envelope>
```

<br />
