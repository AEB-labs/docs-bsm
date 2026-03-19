---
title: Transfer addresses
deprecated: false
hidden: false
metadata:
  robots: index
next:
  description: Go on with materials.
  pages:
    - slug: transfer-materials
      title: Transfer materials
      type: basic
---
In the following you can see an API-Call of transfer Addresses with one address.

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
        [transferAdresses](https://rz3.aeb.de/test2bsm/swagger/#/O%26P/transferAddresses)
      </td>
    </tr>

    <tr>
      <td>
        SOAP
      </td>

      <td>
        [Origin&PreferencesBF (WSDL)](https://rz3.aeb.de/test2bsm/servlet/bf/OriginAndPreferencesBF?WSDL)
        [transferAddresses (Java Doc)](https://rz3.aeb.de/test2bsm/servlet/bf/doc/OriginAndPreferencesBF/de/aeb/xnsg/onpintegration/bf/onp/IOriginAndPreferencesBF.html#transferAddresses\(de.aeb.xnsg.onpintegration.bf.onp.TransferAddressesRequestDTO\))
      </td>
    </tr>
  </tbody>
</Table>

```json
{
  "clientSystemId": "E01_400",
  "clientIdentCode": "{{client}}",
  "userName": "{{user}}",
  "resultLanguageIsoCodes": [
    "en",
    "de"
  ],
  "adressRequests": [
    {
      "idHost" : "su_10004",
      "isDeleted" : false,
      "labelHost": "Lieferantennr.: 1004",
      "reference": "su_1004",
      "addressNo": "1004",
      "city" : "Paris",
      "contactPerson": "Franz",
      "contactPersonTitle" : "Mr.",
      "country": "DE",
      "createProof" : true,
      "defaultPrefVerificationType": null,
      "department": null,
      "dunsNo" : null,
      "email" : null,
      "faxNo" : null,
      "language" : "DE",
      "name1" : "UEC Saturn",
      "name2" : "UEC Saturn2",
      "name3" : "UEC Saturn3",
      "name4" : "UEC Saturn4",
      "outputType": null,
      "postBox" : "71088",
      "postBoxCity" : "Paris",
      "postCodePostbox" : "71099",
      "postCodeStreet" : null,
      "role" : "su",
      "streetAndNo" : "644 Rue Morgue",
      "supplierPriority" : null,
      "telephoneNo": null
    }
  ]
}
```
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
      "idHost": "su_10004"
    }
  ]
}
```
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
        },
        {
          "languageISOCode": "de",
          "text": "Das Pflichtfeld \"idHost\" muss gefüllt sein."
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

<br />
