---
title: Synchronize recheck events
deprecated: false
hidden: false
metadata:
  robots: index
---
A _recheck event_ is the event that is triggered when an user clicks the _check again_ button in the [Compliance-Monitor](https://docs.aeb.com/doc/cm-287937803-923804811-en-US/t-923804811-288528523-en-US).

Similar to the _changed check results_, the compliance API provides two functions to handle these changes:

* getChangedRecheckEvents
* acknowledgeChangedRecheckEvents

<br />

## getChangedRecheckEvents

The function getChangedRecheckEvents can be used to fetch the events.

| API  | Function                                                                                                                                                                                                                                                                                                                      |
| ---- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| REST | POST getChangedRecheckEvents                                                                                                                                                                                                                                                                                                  |
| SOAP | [ComplianceBF (WSDL)](https://rz3.aeb.de/test2bsm/servlet/bf/ComplianceBF?WSDL)  \| <Anchor label=" getChangedCheckResults (JavaDoc)" target="_blank" href="https://rz3.aeb.de/test1bsm/servlet/bf/doc/ComplianceBF/de/aeb/xnsg/bsm/compliance/bf/checkrequest/IComplianceBF.html"> getChangedCheckResults (JavaDoc)</Anchor> |

```
```

<br />
