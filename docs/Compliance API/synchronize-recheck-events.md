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
| REST | [POST getChangedRecheckEvents](https://rz3.aeb.de/test2bsm/swagger/)                                                                                                                                                                                                                                                          |
| SOAP | [ComplianceBF (WSDL)](https://rz3.aeb.de/test2bsm/servlet/bf/ComplianceBF?WSDL)  \| <Anchor label=" getChangedCheckResults (JavaDoc)" target="_blank" href="https://rz3.aeb.de/test2bsm/servlet/bf/doc/ComplianceBF/de/aeb/xnsg/bsm/compliance/bf/checkrequest/IComplianceBF.html"> getChangedCheckResults (JavaDoc)</Anchor> |

The function expects the system id of the pre-system, the BSM client and an username

```json
{
  "clientSystemId": "BRUYES",
  "clientIdentCode": "SAP_JNH_080",
  "userName": "API_TEST",
  "resultLanguageIsoCodes": [
    "en"
  ],
}
```
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:de.aeb.xnsg.bsm.compliance.bf.checkrequest">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:getCheckResult>
         <request>
            <clientSystemId>BRUYES</clientSystemId>
            <clientIdentCode>SAP_JNH_080</clientIdentCode>
            <userName>API_TEST</userName>
            <resultLanguageIsoCodes>en</resultLanguageIsoCodes>
         </request>
      </urn:getCheckResult>
   </soapenv:Body>
</soapenv:Envelope>
```

The result returns all business objects for which the _check again_ button was clicked:

```json
{
  "hasErrors": false,
  "hasOnlyRetryableErrors": false,
  "hasWarnings": false,
  "messages": [],
  "syncId": "354",
  "isComplete": true,
  "recheckEvents": [
    {
      "boIdClientSystem": "SAP_JNH_080_SALES_ORDER_32",
      "boIdClientSystemLabel": "SAP JNH 080 Sales order 32",
      "referenceNumber": "32"
    }
  ]
}
```
```xml
<?xml version="1.0" encoding="UTF-8"?>
<S:Envelope xmlns:S="http://schemas.xmlsoap.org/soap/envelope/">
    <S:Body>
        <ns2:getChangedRecheckEventsResponse xmlns:ns2="urn:de.aeb.xnsg.bsm.compliance.bf.checkrequest">
            <result>
                <hasErrors>false</hasErrors>
                <hasOnlyRetryableErrors>false</hasOnlyRetryableErrors>
                <hasWarnings>false</hasWarnings>
                <syncId>354</syncId>
                <isComplete>true</isComplete>
                <recheckEvents>
                    <boIdClientSystem>SAP_JNH_080_SALES_ORDER_32</boIdClientSystem>
                    <boIdClientSystemLabel>SAP JNH 080 Sales order 32</boIdClientSystemLabel>
                    <referenceNumber>32</referenceNumber>
                </recheckEvents>
            </result>
        </ns2:getChangedRecheckEventsResponse>
    </S:Body>
</S:Envelope>
```

After you handled the event you can use the _syncId_ to confirm it.

<br />

## acknowledgeChangedRecheckEvents

Similar to the _check results_, the function can be used to acknowledge the recheck events.

| API  | Function                                                                                                                                                                                                                                                                                                                  |
| ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| REST | POST acknowledgeChangedRecheckEvents                                                                                                                                                                                                                                                                                      |
| SOAP | [ComplianceBF (WSDL)](https://rz3.aeb.de/test2bsm/servlet/bf/ComplianceBF?WSDL)  \| <Anchor label="acknowledgeChangedRecheckEvents" target="_blank" href="https://rz3.aeb.de/test2bsm/servlet/bf/doc/ComplianceBF/de/aeb/xnsg/bsm/compliance/bf/checkrequest/IComplianceBF.html">acknowledgeChangedRecheckEvents</Anchor> |

To call the function, you need to provide the system id of the pre-system, the BSM client, a username and the _syncId_ that is provided by the response of the _getChangedRecheckEvents_ function.

```json
{
  "clientSystemId": "BRUYES",
  "clientIdentCode": "SAP_JNH_080",
  "userName": "API_TEST",
  "resultLanguageIsoCodes": [
    "en"
  ],
  "syncId": "354"
}
```
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:de.aeb.xnsg.bsm.compliance.bf.checkrequest">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:acknowledgeChangedRecheckEvents>
         <request>
            <clientSystemId>BRUYES</clientSystemId>
            <clientIdentCode>SAP_JNH_080</clientIdentCode>
            <userName>API_TEST</userName>
            <resultLanguageIsoCodes>en</resultLanguageIsoCodes>
            <syncId>354</syncId>
         </request>
      </urn:acknowledgeChangedRecheckEvents>
   </soapenv:Body>
</soapenv:Envelope>

```

The result will look like the response body below:

```json
{
  "hasErrors": false,
  "hasOnlyRetryableErrors": false,
  "hasWarnings": false,
  "messages": []
}
```
```xml
<?xml version="1.0" encoding="UTF-8"?>
<S:Envelope xmlns:S="http://schemas.xmlsoap.org/soap/envelope/">
    <S:Body>
        <ns2:acknowledgeChangedRecheckEventsResponse xmlns:ns2="urn:de.aeb.xnsg.bsm.compliance.bf.checkrequest">
            <result>
                <hasErrors>false</hasErrors>
                <hasOnlyRetryableErrors>false</hasOnlyRetryableErrors>
                <hasWarnings>false</hasWarnings>
            </result>
        </ns2:acknowledgeChangedRecheckEventsResponse>
    </S:Body>
</S:Envelope>
```
