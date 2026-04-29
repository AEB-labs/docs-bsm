---
title: Delete the Check Results
deprecated: false
hidden: false
metadata:
  robots: index
---
After performing a check request you will be able to delete the check requests of a business object. Therefore, you can use the function below:

| API  | Function                                                                                                                                                                                                                                                                                      |
| ---- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| REST | POST delete                                                                                                                                                                                                                                                                                   |
| SOAP | [ComplianceBF (WSDL)](https://rz3.aeb.de/test2bsm/servlet/bf/ComplianceBF?WSDL)  \| <Anchor label=" delete (JavaDoc)" target="_blank" href="https://rz3.aeb.de/test1bsm/servlet/bf/doc/ComplianceBF/de/aeb/xnsg/bsm/compliance/bf/checkrequest/IComplianceBF.html"> delete (JavaDoc)</Anchor> |

<br />

The function requires the system id of the pre-system (_clientSystemid_), the BSM client (_clientIdentCode_), a user name and the ID of the business object you want to delete:

```
{
  "clientSystemId": "BRUYES",
  "clientIdentCode": "{{client}}",
  "userName": "{{user}}",
  "resultLanguageIsoCodes": [
    "en"
  ],
  "boIdClientSystem": "{{boIdClientSystem}}"  
}
```

<br />
