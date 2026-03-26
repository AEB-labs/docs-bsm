---
title: Transfer materials
deprecated: false
hidden: false
metadata:
  robots: index
next:
  description: Go on with bill of materials.
  pages:
    - slug: transfer-bill-of-materials
      title: Transfer bill of materials
      type: basic
---
<br />

In the following you can see an API-Call of transfer materials with one material.

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
        <Anchor label="transferMaterials" target="_blank" href="https://rz3.aeb.de/test2bsm/swagger/#/O%26P/transferMaterials">transferMaterials</Anchor>
      </td>
    </tr>

    <tr>
      <td>
        SOAP
      </td>

      <td>
        <Anchor label="Origin&PreferencesBF (WSDL)" target="_blank" href="https://rz3.aeb.de/test2bsm/servlet/bf/OriginAndPreferencesBF?WSDL">Origin&PreferencesBF (WSDL)</Anchor>
        <Anchor label="transferMaterials (Java Doc)" target="_blank" href="https://rz3.aeb.de/test2bsm/servlet/bf/doc/OriginAndPreferencesBF/de/aeb/xnsg/onpintegration/bf/onp/IOriginAndPreferencesBF.html#transferMaterials(de.aeb.xnsg.onpintegration.bf.onp.TransferMaterialsRequestDTO)">transferMaterials (Java Doc)</Anchor>
      </td>
    </tr>
  </tbody>
</Table>

```json
{
  "clientSystemId": "ERP_SYSTEM_X",
  "clientIdentCode": "API_TEST",
  "userName": "API_TEST",
  "resultLanguageIsoCodes": [
    "en"
  ],
  "materialRequests": [
    {
      "idHost": "MAT-1",
      "labelHost": "MAT-1",
      "organizationalUnit": "1000",
      "referenceNo": "Mat-1",
      "isDeleted": true,     
      "materialNo": "Mat-1",
      "materialNoInternal": "Mat-1",
      "isActive": true,
      "factoryType": "i",
      "materialPriority": 1,
      "commodityCode1": "010121051",
      "commodityCode2": "010121051",
      "commodityCode3": "010121051",
      "purchaseValue": 100,
      "lotSize": 1,
      "currency": "EUR",
      "quantityUnit": "ST",
      "isRelavantForCalculation": true,
      "averageStorage": 0,
      "mainDescriptionLanguage": "EN",
      "orderItemReference": null,
      "isCompositionOfGoods": false,
      "requestMaterial": "1",
      "isConfigured": true,
      "nonPreferentialOriginCountry": "DE",
      "descriptions": [
        {
          "description": "EN Description",
          "isDeleted": true,
          "language": "EN"
        }
      ],
      "materialType": "HAWA",
      "quantities": [
        {
          "type": "string",
          "quantity": {
            "value": 999999999999.999,
            "unit": "kg"
          }
        }
      ]
    }
  ]
}

```
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:de.aeb.xnsg.onpintegration.bf.onp">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:transferMaterials>
         <request>
              <clientIdentCode>{{client}}</clientIdentCode>
                <clientSystemId>YLI_POSTMAN</clientSystemId>
                <resultLanguageIsoCodes>EN</resultLanguageIsoCodes>
                <userName>{{user}}</userName>
                   <materialRequests>
                 <idHost>MAT-1</idHost>
                 <labelHost>MAT-1</labelHost>
                 <organizationalUnit>10001</organizationalUnit>
                 <referenceNo>MAT-1</referenceNo>
                 <isDeleted>false</isDeleted>
                 <materialNo>MAT</materialNo>
                 <isActive>true</isActive>
                 <factoryType>i</factoryType>
                 <materialPriority>1</materialPriority>
                 <commodityCode1>010121051</commodityCode1>
                 <commodityCode2>010121051</commodityCode2>
                 <commodityCode3>010121051</commodityCode3>
                 <purchaseValue>1.23</purchaseValue>
                 <lotSize>5</lotSize>
                 <currency>EUR</currency>
                 <quantityUnit>ST</quantityUnit>
                 <isRelavantForCalculation>true</isRelavantForCalculation>
                 <averageStorage>7</averageStorage>
                 <mainDescriptionLanguage>DE</mainDescriptionLanguage>
                 <orderItemReference>4711_10</orderItemReference>
                 <isCompositionOfGoods>true</isCompositionOfGoods>
                 <requestMaterial>1</requestMaterial>
                 <isConfigured>true</isConfigured>
                 <nonPreferentialOriginCountry>CH</nonPreferentialOriginCountry>
                 <descriptions>
                    <description>DE Textä</description>
                    <isDeleted>false</isDeleted>
                    <language>DE</language>
                 </descriptions>
              </materialRequests>
         </request>
      </urn:transferMaterials>
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
      "idHost": "MAT-1"
    }
  ]
}
```
```xml
<?xml version="1.0" encoding="UTF-8"?>
<S:Envelope xmlns:S="http://schemas.xmlsoap.org/soap/envelope/">
    <S:Body>
        <ns2:transferMaterialsResponse xmlns:ns2="urn:de.aeb.xnsg.onpintegration.bf.onp">
            <result>
                <hasErrors>false</hasErrors>
                <hasOnlyRetryableErrors>false</hasOnlyRetryableErrors>
                <hasWarnings>false</hasWarnings>
                <responses>
                    <hasErrors>false</hasErrors>
                    <hasWarnings>false</hasWarnings>
                    <idHost>MAT-1</idHost>
                </responses>
            </result>
        </ns2:transferMaterialsResponse>
    </S:Body>
</S:Envelope>
```

In case of an error it looks like this.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<S:Envelope xmlns:S="http://schemas.xmlsoap.org/soap/envelope/">
    <S:Body>
        <ns2:transferMaterialsResponse xmlns:ns2="urn:de.aeb.xnsg.onpintegration.bf.onp">
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
        </ns2:transferMaterialsResponse>
    </S:Body>
</S:Envelope>
```
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
