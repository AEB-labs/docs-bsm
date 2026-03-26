---
title: Get changed material master data
deprecated: false
hidden: false
metadata:
  robots: index
next:
  description: 'Now you can try to get an declaration of origin. '
  pages:
    - slug: declaration-of-origin
      title: Declaration of origin
      type: basic
---
If you like to synchronize the material master data e.g. to persist the data in the erp system you should use our getChangedMaterialMasterData-API. The logic of your program could look like this:

* call getChangedMaterialMasterData
* persist the data of the response
* check if the isComplete-Flag is true
* if yes call acknowledgeGetChangedMaterialMasterData with the syncId given in getChangedMaterialMasterData
* If no call getChangedMaterialMasterData again

Ok and now let's do that in detail with some sample calls. So as i sad first we call getChangedMaterialMasterData.

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
        <Anchor label="getChangedMaterialMasterData" target="_blank" href="https://rz3.aeb.de/test2bsm/swagger/#/O%26P/getChangedMaterialMasterData">getChangedMaterialMasterData</Anchor>
      </td>
    </tr>

    <tr>
      <td>
        SOAP
      </td>

      <td>
        <Anchor label="Origin&PreferencesBF (WSDL)" target="_blank" href="https://rz3.aeb.de/test2bsm/servlet/bf/OriginAndPreferencesBF?WSDL">Origin&PreferencesBF (WSDL)</Anchor>
        <Anchor label="getChangedMaterialMasterData (Java Doc)" target="_blank" href="https://rz3.aeb.de/test2bsm/servlet/bf/doc/OriginAndPreferencesBF/de/aeb/xnsg/onpintegration/bf/onp/IOriginAndPreferencesBF.html#getChangedMaterialMasterData(de.aeb.xnsg.onpintegration.bf.onp.GetChangedMaterialMasterDataRequestDTO)">getChangedMaterialMasterData (Java Doc)</Anchor>
      </td>
    </tr>
  </tbody>
</Table>

```json
`{
  "clientSystemId": "ERP_SYSTEM_ID",
  "clientIdentCode": "AEB_TEST_CLIENT",
  "userName": "user",
  "resultLanguageIsoCodes": [
    "en"
  ]
}
```
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:de.aeb.xnsg.onpintegration.bf.onp">
    <soapenv:Header/>
    <soapenv:Body>
        <urn:getChangedMaterialMasterData>
            <request>
                <clientIdentCode>{{client}}</clientIdentCode>
                <clientSystemId>E01_400</clientSystemId>
                <resultLanguageIsoCodes>DE</resultLanguageIsoCodes>
                <resultLanguageIsoCodes>EN</resultLanguageIsoCodes>
                <userName>{{user}}</userName>
            </request>
        </urn:getChangedMaterialMasterData>
    </soapenv:Body>
</soapenv:Envelope>
```

The answer of this call could then look like this.

```json
`{
  "hasErrors": false,
  "hasOnlyRetryableErrors": false,
  "hasWarnings": false,
  "messages": [],
  "syncId": "8",
  "isComplete": true,
  "materialMasterData": [
    {
      "materialNo": "MAT",
      "orderItemReference": "4711_10",
      "destinationCountry": "US",
      "sourceCountry1": "CE",
      "sourceCountry2": "CH",
      "commodityCode1": "010121051",
      "minimumSalesValue": 999999999,
      "cummulationType": "1",
      "currency": "EUR",
      "isLogicalDeleted": false
    },
    {
      "materialNo": "MAT",
      "orderItemReference": "4711_10",
      "destinationCountry": "DE",
      "sourceCountry1": "CE",
      "sourceCountry2": "CH",
      "commodityCode1": "010121051",
      "minimumSalesValue": 999999999,
      "cummulationType": "2",
      "currency": "EUR",
      "isLogicalDeleted": false
    }
  ]
}
```
```xml
<?xml version="1.0" encoding="UTF-8"?>
<S:Envelope xmlns:S="http://schemas.xmlsoap.org/soap/envelope/">
    <S:Body>
        <ns2:getChangedMaterialMasterDataResponse xmlns:ns2="urn:de.aeb.xnsg.onpintegration.bf.onp">
            <result>
                <hasErrors>false</hasErrors>
                <hasOnlyRetryableErrors>false</hasOnlyRetryableErrors>
                <hasWarnings>false</hasWarnings>
                <syncId>8</syncId>
                <isComplete>true</isComplete>
                <materialMasterData>
                    <materialNo>000000000000000031</materialNo>
                    <destinationCountry>DE</destinationCountry>
                    <sourceCountry1>CE</sourceCountry1>
                    <minimumSalesValue>999999999.000</minimumSalesValue>
                    <cummulationType>2</cummulationType>
                    <currency>EUR</currency>
                    <isLogicalDeleted>true</isLogicalDeleted>
                </materialMasterData>
                <materialMasterData>
                    <materialNo>M-11</materialNo>
                    <destinationCountry>US</destinationCountry>
                    <sourceCountry1>CE</sourceCountry1>
                    <commodityCode1>84185011</commodityCode1>
                    <minimumSalesValue>999999999.000</minimumSalesValue>
                    <cummulationType>1</cummulationType>
                    <currency>EUR</currency>
                    <isLogicalDeleted>false</isLogicalDeleted>
                </materialMasterData>
            </result>
        </ns2:getChangedMaterialMasterDataResponse>
    </S:Body>
</S:Envelope>
```

As you can see the isComplete is set to true and the syncId is 8. So let's do the acknowledge-API call.

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
        [acknowledgeGetChangedMaterialMasterData](https://rz3.aeb.de/test2bsm/swagger/#/O%26P/acknowledgeGetChangedMaterialMasterData)
      </td>
    </tr>

    <tr>
      <td>
        SOAP
      </td>

      <td>
        [Origin&PreferencesBF (WSDL)](https://rz3.aeb.de/test2bsm/servlet/bf/OriginAndPreferencesBF?WSDL)
        [acknowledgeGetChangedMaterialMasterData (Java Doc)](https://rz3.aeb.de/test2bsm/servlet/bf/doc/OriginAndPreferencesBF/de/aeb/xnsg/onpintegration/bf/onp/IOriginAndPreferencesBF.html#acknowledgeGetChangedMaterialMasterData\(de.aeb.xnsg.onpintegration.bf.onp.acknowledgeGetChangedMaterialMasterDataRequestDTO\))
      </td>
    </tr>
  </tbody>
</Table>

```json
`{
  "clientSystemId": "ERP_SYSTEM_ID",
  "clientIdentCode": "AEB_TEST_CLIENT",
  "userName": "user",
  "syncId" : 8,
  "resultLanguageIsoCodes": [
    "en",
    "de"
  ]
}

```
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:de.aeb.xnsg.onpintegration.bf.onp">
    <soapenv:Header/>
    <soapenv:Body>
        <urn:acknowledgeGetChangedMaterialMasterData>
            <request>
                <clientIdentCode>API_TEST_CLIENT</clientIdentCode>
                <clientSystemId>ERP_SYSTEM_ID</clientSystemId>
                <resultLanguageIsoCodes>EN</resultLanguageIsoCodes>
                <userName>API_TEST_USER</userName>
               <syncId>8</syncId>
            </request>
        </urn:acknowledgeGetChangedMaterialMasterData>
    </soapenv:Body>
</soapenv:Envelope>
```

If you now call the getChangedMaterialMasterData-API again no data will return.

<br />
