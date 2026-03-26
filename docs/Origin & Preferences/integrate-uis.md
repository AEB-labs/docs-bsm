---
title: Integrate UIs
deprecated: false
hidden: false
metadata:
  robots: index
---
If you like to integrate the material master data search you can use the following API.

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
        <Anchor label="OpenMaterialMasterDataSearchUI" target="_blank" href="https://rz3.aeb.de/test2bsm/swagger/#/O%26P/openMaterialMasterDataSearchUI">OpenMaterialMasterDataSearchUI</Anchor>
      </td>
    </tr>

    <tr>
      <td>
        SOAP
      </td>

      <td>
        <Anchor label="Origin&PreferencesAF (WSDL)" target="_blank" href="https://rz3.aeb.de/test2bsm/servlet/bf/OriginAndPreferencesAF?WSDL">Origin&PreferencesAF (WSDL)</Anchor>
        <Anchor label="openMaterialMasterDataSearch (Java Doc)" target="_blank" href="https://rz3.aeb.de/test2bsm/servlet/bf/doc/OriginAndPreferencesAF/de/aeb/xnsg/onpintegration/af/onp/IOriginAndPreferencesAF.html#openMaterialMasterDataSearch(de.aeb.xnsg.foundation.af.ApplicationFacadeParmsDTO,de.aeb.xnsg.onpintegration.af.onp.ONPMaterialMasterDataSearchDTO)">openMaterialMasterDataSearch (Java Doc)</Anchor>
      </td>
    </tr>
  </tbody>
</Table>

```json
{
  "clientSystemId": "TEST_ID",
  "clientIdentCode": "{{client}}",
  "userName": "API_TEST",
  "resultLanguageIsoCodes": [
    "en"
  ],
  "searchDTO": {
    "storedFilterName": "filterName123"
  }
}
```
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:de.aeb.xnsg.onpintegration.af.onp">
    <soapenv:Header/>
    <soapenv:Body>
        <urn:openMaterialMasterDataSearch>
            <parmsDTO>
                <clientIdentCode>{{client}}</clientIdentCode>
                <clientSystemId>E01_400</clientSystemId>
                <resultLanguageIsoCodes>DE</resultLanguageIsoCodes>
                <resultLanguageIsoCodes>EN</resultLanguageIsoCodes>
                <userName>{{user}}</userName>
            </parmsDTO>
            <searchDTO>
                <storedFilterName>null</storedFilterName>
            </searchDTO>
        </urn:openMaterialMasterDataSearch>
    </soapenv:Body>
</soapenv:Envelope>
```

And the response of the API-Call looks like this.

```json
{
  "sessionid": "AFCall-Invoke4543994161773980227668",
  "httpUrl": "http://localhost:17080/bsm/servlet/LazyStartAF?call=Invoke4543994161773980227668",
  "urlCloseToken": "goodbypage"
}
```
```xml
<?xml version="1.0" encoding="UTF-8"?>
<S:Envelope xmlns:S="http://schemas.xmlsoap.org/soap/envelope/">
    <S:Body>
        <ns2:openMaterialMasterDataSearchResponse xmlns:ns2="urn:de.aeb.xnsg.onpintegration.af.onp">
            <result>
                <httpUrl>https://xnsg.dev.aeb.com/dev1bsm/servlet/LazyStartAF?call=Invoke7311793861773934635691</httpUrl>
                <sessionid>AFCall-Invoke7311793861773934635691</sessionid>
                <urlCloseToken>goodbypage</urlCloseToken>
            </result>
        </ns2:openMaterialMasterDataSearchResponse>
    </S:Body>
</S:Envelope>
```

Just use the httpUrl and open it in a browser tab.
