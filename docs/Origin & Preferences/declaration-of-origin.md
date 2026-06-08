---
title: Declaration of origin
deprecated: false
hidden: false
metadata:
  robots: index
next:
  description: 'Ok last but not least, you can integrate our UIs. '
  pages:
    - slug: integrate-uis
      title: Integrate UIs
      type: basic
---
If you require a declaration of origin on your invoice document, or need to verify whether a transaction qualifies for preferential treatment, you can use the `getDeclarationOfOrigin` API as shown below.

| Technique | Documentation                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| --------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| REST      | <Anchor label="GetDeclarationOfOrigin" target="_blank" href="https://rz3.aeb.de/test2bsm/swagger/#/O%26P/getDeclarationOfOrigin">GetDeclarationOfOrigin</Anchor>                                                                                                                                                                                                                                                                                                                                                                                          |
| SOAP      | <Anchor label="DeclarationOfOriginBF (WSDL)" target="_blank" href="https://rz3.aeb.de/test2bsm/servlet/bf/DeclarationOfOriginBF?WSDL">DeclarationOfOriginBF (WSDL)</Anchor> \| <Anchor label="getDeclarationOfOrigin (Java Doc)" target="_blank" href="https://rz3.aeb.de/test2bsm/servlet/bf/doc/DeclarationOfOriginBF/de/aeb/xnsg/onpintegration/bf/declarationoforigin/IDeclarationOfOriginBF.html#getDeclarationOfOrigin(de.aeb.xnsg.onpintegration.bf.declarationoforigin.DeclarationOfOriginRequestDTO)">getDeclarationOfOrigin (Java Doc)</Anchor> |

```json
{
  "clientSystemId": "TEST_ID",
  "clientIdentCode": "{{client}}",
  "userName": "API_TEST",
  "resultLanguageIsoCodes": [
    "en"
  ],
  "organizationalUnit": "1000",
  "referenceNo": "4711",
  "idHost": "4711",
  "labelHost": "4711",
  "destinationCountry": "CH",
  "documentDate": "2026-01-27",
  "place": "Stuttgart",
  "remarks": "vermerk",
  "signatoryName": "Peter",
  "documentLanguageIso": "DE",
  "isInvoiceSigned": true,
  "isDateAndPlacePresentAtInvoice": true,
  "mainOrganizationalUnit": "1000",
  "sourceCountry": "DE",
  "validFrom": "2026-01-27",
  "validTo": "2028-01-27",
  "nameOfExporter": "NameOfExp",
  "factoryPriceCurrency": "DE",
  "serialNumber": null,
  "declarationOfOriginType": null,
  "items": [
    {
      "itemNo": "1",
      "materialNo": "M-11",
      "materialNoInternal": "M-11",
      "materialOrderItemReference": null,
      "factoryPrice": 1111,
      "quantity": 1
    }
  ]
}

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
{
  "hasErrors": false,
  "hasOnlyRetryableErrors": false,
  "hasWarnings": false,
  "messages": [],
  "text": "Der Ausführer der Waren, auf die sich dieses Handelspapier bezieht, erklärt, dass diese Waren, soweit nicht anders angegeben, präferenzbegünstigte EU Ursprungswaren sind.\n\nStuttgart, 27.01.2026\n(Ort und Datum)\n________________________________________ Peter\n(Unterschrift des Ausführers und Name des Unterzeichneten in Druckschrift)",
  "isDeclarationOfOriginAllowed": true,
  "isDeclarationOfOriginToSign": true,
  "items": [
    {
      "itemNo": "1",
      "text": "- Präferenzieller Ursprung: EU",
      "hasPreference": true,
      "preferentialOrigin": "EU"
    }
  ],
  "linkToDeclOfOriginCheckLog": "https://origin-preferences-management-test.internal.aeb.com/doo/home/protocols/doo-sap/view/468?system=0bbcdf2c000ff8c"
}
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
