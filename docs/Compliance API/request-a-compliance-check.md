---
title: Request a Compliance Check
deprecated: false
hidden: false
metadata:
  robots: index
---
You can use the the Compliance API to check a business object. This check contains compliance screening and export controls.

If you are interested in learning more about Compliance Screening or Export Controls, you can find additional information here:

* **Compliance Screening:** [https://docs.aeb.com/doc/cm-287937803-923804811-en-US/t-923804811-288463499-en-US](https://docs.aeb.com/doc/cm-287937803-923804811-en-US/t-923804811-288463499-en-US)
* **Export Controls:** [https://docs.aeb.com/doc/cm-287939723-996830731-en-US/t-996830731-288627211-en-US](https://docs.aeb.com/doc/cm-287939723-996830731-en-US/t-996830731-288627211-en-US)

<br />

To check a business object, you can use the following function:

| API  | Function                                                                                                                                                                                                                                                                                                                         |
| ---- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| REST | requestCheck                                                                                                                                                                                                                                                                                                                     |
| SOAP | [ComplianceBF (WSDL)](https://rz3.aeb.de/test2bsm/servlet/bf/ComplianceBF?WSDL)  \| <Anchor label="requestCheck (JavaDoc)" target="_blank" href="https://rz3.aeb.de/test2bsm/servlet/bf/doc/ComplianceBF/de/aeb/xnsg/bsm/compliance/bf/checkrequest/ComplianceBusinessObjectCheckResultDTO.html">requestCheck (JavaDoc)</Anchor> |

<br />

```json JSON
{
  "clientSystemId": "BRUYES",
  "clientIdentCode": "API_TEST_CLIENT",
  "userName": "API_TEST",
  "resultLanguageIsoCodes": [
    "en"
  ],
  "boIdClientSystem": "UNIQUE_BO_ID",
  "boIdClientSystemLabel": "UNIQUE_BO_ID_READBLE",
  "referenceNumber": "REFERENCE_NUMBER",
  "businessObjectType": "BUSINESS_OBJECT_TYPE",
  "mappingProfile": "CMP_MAPPING_PROFILE",
  "parties": [
    {
      "orgUnits": [
        "ORG_UNIT"
      ],
      "roleIdentCode": "",
      "name1": "United Aircraft Corporation",
      "street": "Ulansky side-street 22",
      "city": "Moscow",
      "postalCode": "101000",
      "countryIso": "RU",
      "companyReference": "United_Aircraft_Corporation",
      "addressType": "3"
    }
  ],
  "monitorParty": {
    "roleIdentCode": "",
    "companyReference": "United_Aircraft_Corporation"
  },
  "forceCheck": false
}
```
```xml XML
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:de.aeb.xnsg.bsm.compliance.bf.checkrequest">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:requestCheck>
         <request>
            <clientSystemId>BRUYES</clientSystemId>
            <clientIdentCode>API_TEST_CLIENT</clientIdentCode>
            <userName>API_TEST</userName>
            <resultLanguageIsoCodes>EN</resultLanguageIsoCodes>
            <boIdClientSystem>UNIQUE_BO_ID</boIdClientSystem>
            <boIdClientSystemLabel>UNIQUE_BO_ID_READBLE</boIdClientSystemLabel>
            <referenceNumber>REFERENCE_NUMBER</referenceNumber>
            <businessObjectType>BUSINESS_OBJECT_TYPE</businessObjectType>
            <mappingProfile>CMP_MAPPING_PROFILE</mappingProfile>
            <parties>
               <orgUnits>ORG_UNIT</orgUnits>
               <roleIdentCode></roleIdentCode>
               <name1>United Aircraft Corporation</name1>
               <street>Ulansky side-street 22</street>
               <city>Moscow</city>
               <postalCode>101000</postalCode>
               <countryIso>RU</countryIso>
               <companyReference>United_Aircraft_Corporation</companyReference>
            </parties>
           <monitorParty>
             <roleIdentCode></roleIdentCode>
             <companyReference>United_Aircraft_Corporation</companyReference>
           </monitorParty>
           <forceCheck>false</forceCheck>
         </request>
      </urn:requestCheck>
   </soapenv:Body>
</soapenv:Envelope>
```

<br />

<br />
