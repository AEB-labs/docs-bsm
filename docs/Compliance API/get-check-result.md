---
title: Get Check Result
deprecated: false
hidden: false
metadata:
  robots: index
---
You can fetch the check results of a business object by executing the following function:

| API  | Function                                                                                                                                                                                                                                                                                                      |
| ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| REST | POST getCheckResult                                                                                                                                                                                                                                                                                           |
| SOAP | [ComplianceBF (WSDL)](https://rz3.aeb.de/test2bsm/servlet/bf/ComplianceBF?WSDL)  \| <Anchor label=" getCheckResult (JavaDoc)" target="_blank" href="https://rz3.aeb.de/test1bsm/servlet/bf/doc/ComplianceBF/de/aeb/xnsg/bsm/compliance/bf/checkrequest/IComplianceBF.html"> getCheckResult (JavaDoc)</Anchor> |

<br />

To execute the function, you' have to provide the system id of the pre-system (_clientSystemid_), the BSM client (_clientIdentCode_), a user name and the ID of the business object you want to fetch:

```json
{
  "clientSystemId": "BRUYES",
  "clientIdentCode": "{{client}}",
  "userName": "API_TEST",
  "resultLanguageIsoCodes": [
    "en"
  ],
  "boIdClientSystem": "{{boIdClientSystem}}"  
}
```
```xml
```
