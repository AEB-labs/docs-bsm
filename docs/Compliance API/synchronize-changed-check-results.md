---
title: Synchronize changed check results
deprecated: false
hidden: false
metadata:
  robots: index
---
After performing a check, the status of the check result may change. For instance, you executed a screening check that leads to a _critical_ check result. Defining a good guy for the critical address will change the compliance status to _not critical_.

The Compliance API provides to functions to handle these changes:

* getChangedCheckResults
* acknowledgeChangedCheckResults

<br />

## getChangedCheckResults

The function getChangedCheckResults can be used to fetch the changes.

| API  | Function                                                                                                                                                                                                                                                                                                                      |
| ---- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| REST | POST getChangedCheckResults                                                                                                                                                                                                                                                                                                   |
| SOAP | [ComplianceBF (WSDL)](https://rz3.aeb.de/test2bsm/servlet/bf/ComplianceBF?WSDL)  \| <Anchor label=" getChangedCheckResults (JavaDoc)" target="_blank" href="https://rz3.aeb.de/test1bsm/servlet/bf/doc/ComplianceBF/de/aeb/xnsg/bsm/compliance/bf/checkrequest/IComplianceBF.html"> getChangedCheckResults (JavaDoc)</Anchor> |

<br />

```json
```

<br />

<br />
