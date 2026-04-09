---
title: Request a Compliance Check
deprecated: false
hidden: false
metadata:
  robots: index
---
You can use the the Compliance API to check a business object. This check contains compliance screening and export controls.

If you are interested in learning more about Compliance Screening or Export Controls, you can find additional information here:

* **Compliance Screening:** https://docs.aeb.com/doc/cm-287937803-923804811-en-US/t-923804811-288463499-en-US
* **Export Controls:** https://docs.aeb.com/doc/cm-287939723-996830731-en-US/t-996830731-288627211-en-US

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
  "userName": "API_TEST_USER",
  "resultLanguageIsoCodes": [
    "DE, "EN"
  ],
  "boIdClientSystem": "X360_X360-Test-System:BEX_CUSTOMER_DEBITOR202",
  "boIdClientSystemLabel": "UNIQUE_BO_ID_CLIENT_SYSTEM_LABEL",
  "referenceNumber": "DEBITOR202",
  "businessObjectType": "<EXISTING_BO_TYPE>",
  "mappingProfile": "<EXISTING_MAPPING_PROFILE>",
  "parties": [
    {
      "orgUnits": [
        "SALES"
      ],
      "roleIdentCode": "",
      "name1": "Wladimir Putin",
      "street": "Straße 20",
      "city": "Ulm",
      "postalCode": "73447",
      "countryIso": "DE",
      "companyReference": "MainContact_Wladimir Putin",
      "addressType": "3"
    }
  ],
  "blockMemories": [
    {
      "blockIdClientSystem": "Status",
      "blockValue": "Compliance"
    }
  ],
  "monitorParty": {
    "roleIdentCode": "",
    "companyReference": "MainContact_Wladimir Putin"
  },
  "forceCheck": false
}
```
```xml XML
console.log('Code Tab B');
```

<br />

<br />
