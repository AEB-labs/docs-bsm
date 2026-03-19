---
title: Get single material master data
deprecated: false
hidden: false
metadata:
  robots: index
next:
  description: If you like to sync your material master go on with that.
  pages:
    - slug: get-changed-material-master-data
      title: Get changed material master data
      type: basic
---
In the following you can see an API-Call of getting a single material master data.

```json
{
  "clientSystemId": "TEST_ID",
  "clientIdentCode": "{{client}}",
  "userName": "API_TEST",
  "resultLanguageIsoCodes": [
    "en"
  ],
  "materialNo": "AVC_RBT_BUNDLE",
  "materialNoInternal": "AVC_RBT_BUNDLE",
  "destinationCountry": "AG",
  "orderItemReference": null,
  "organizationalUnit": null
}
```
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:de.aeb.xnsg.onpintegration.bf.onp">
    <soapenv:Header/>
    <soapenv:Body>
        <urn:getMaterialMasterData>
            <request>
                <clientIdentCode>{{client}}</clientIdentCode>
                <clientSystemId>YLI_POSTMAN</clientSystemId>
                <resultLanguageIsoCodes>DE</resultLanguageIsoCodes>
                <resultLanguageIsoCodes>EN</resultLanguageIsoCodes>
                <userName>{{user}}</userName>
                <destinationCountry>AG</destinationCountry>
                <materialNo>AVC_RBT_BUNDLE</materialNo>
                <materialNoInternal>AVC_RBT_BUNDLE</materialNoInternal>              
                <orderItemReference></orderItemReference>
            </request>
        </urn:getMaterialMasterData>
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
  "materialMasterData": {
    "materialNo": "10001846-S",
    "destinationCountry": "TT",
    "sourceCountry1": "CE",
    "sourceCountry2": "DE",
    "commodityCode1": "34012090",
    "commodityCode2": "34012090",
    "minimumSalesValue": 0,
    "cummulationType": "1",
    "currency": "EUR",
    "isLogicalDeleted": false
  }
}
```
```xml
<?xml version="1.0" encoding="UTF-8"?>
<S:Envelope xmlns:S="http://schemas.xmlsoap.org/soap/envelope/">
    <S:Body>
        <ns2:getMaterialMasterDataResponse xmlns:ns2="urn:de.aeb.xnsg.onpintegration.bf.onp">
            <result>
                <hasErrors>false</hasErrors>
                <hasOnlyRetryableErrors>false</hasOnlyRetryableErrors>
                <hasWarnings>false</hasWarnings>
                <materialMasterData>
                    <materialNo>AVC_RBT_BUNDLE</materialNo>
                    <destinationCountry>AG</destinationCountry>
                    <sourceCountry1>QU</sourceCountry1>
                    <commodityCode1>28431010</commodityCode1>
                    <minimumSalesValue>999999999.000</minimumSalesValue>
                    <cummulationType>0</cummulationType>
                    <currency>EUR</currency>
                    <isLogicalDeleted>false</isLogicalDeleted>
                </materialMasterData>
            </result>
        </ns2:getMaterialMasterDataResponse>
    </S:Body>
</S:Envelope>
```

<br />
