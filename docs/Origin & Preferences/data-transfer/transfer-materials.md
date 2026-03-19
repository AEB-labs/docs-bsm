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

In the following you can see an API-Call of transfer materials with one material

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