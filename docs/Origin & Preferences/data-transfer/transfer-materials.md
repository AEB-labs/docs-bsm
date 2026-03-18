---
title: Transfer materials
deprecated: false
hidden: false
metadata:
  robots: index
---
<br />

In the following you can see an API-Call of transfer materials with one material

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:de.aeb.xnsg.onpintegration.bf.onp">
    <soapenv:Header/>
    <soapenv:Body>
        <urn:transferAddresses>
            <request>
                <clientIdentCode>AEB_TEST_CLIENT</clientIdentCode>
                <clientSystemId>ERP_SYSTEM_X</clientSystemId>
                <resultLanguageIsoCodes>EN</resultLanguageIsoCodes>
                <userName>userName</userName>
                <adressRequests>
                    <idHost>su_0000001004</idHost>
                    <isDeleted></isDeleted>
                    <labelHost>Mandant: 400 Lieferantennr.: 1004</labelHost>
                    <organizationalUnit>DEFAULT</organizationalUnit>
                    <referenceNo>su_1004</referenceNo>
                    <addressNo>1004</addressNo>
                    <city>Paris</city>
                    <contactPerson></contactPerson>
                    <contactPersonTitle></contactPersonTitle>
                    <country>FR</country>
                    <createProof>true</createProof>
                    <defaultPrefVerificationType></defaultPrefVerificationType>
                    <department></department>
                    <dunsNo></dunsNo>
                    <email></email>
                    <faxNo></faxNo>
                    <language>FR</language>
                    <name1>UEC Saturn</name1>
                    <name2></name2>
                    <name3></name3>
                    <name4></name4>
                    <outputType></outputType>
                    <postBox></postBox>
                    <postBoxCity>Paris</postBoxCity>
                    <postCodePostbox></postCodePostbox>
                    <postCodeStreet>54321</postCodeStreet>
                    <role>su</role>
                    <streetAndNo>644 Rue Morgue</streetAndNo>
                    <supplierPriority></supplierPriority>
                    <telephoneNo></telephoneNo>
                </adressRequests>
            </request>
        </urn:transferAddresses>
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
