---
title: Integrate UIs
deprecated: false
hidden: false
metadata:
  robots: index
---
If you like to integrate the material master data search you can use the following API. 

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
