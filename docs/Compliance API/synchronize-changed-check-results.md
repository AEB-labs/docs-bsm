---
title: Synchronize changed check results
deprecated: false
hidden: false
metadata:
  robots: index
next:
  description: In the next section, you'll learn how to handle recheck events.
  pages:
    - slug: synchronize-recheck-events
      title: Synchronize recheck events
      type: basic
---
After performing a check, the status of the check result may change. For instance, you executed a screening check that leads to a _critical_ check result. Defining a good guy for the critical address will change the compliance status to _not critical_.

The Compliance API provides two functions to handle these changes:

* getChangedCheckResults
* acknowledgeChangedCheckResults

<br />

## getChangedCheckResults

The function getChangedCheckResults can be used to fetch the changes.

| API  | Function                                                                                                                                                                                                                                                                                                                      |
| ---- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| REST | POST getChangedCheckResults                                                                                                                                                                                                                                                                                                   |
| SOAP | [ComplianceBF (WSDL)](https://rz3.aeb.de/test2bsm/servlet/bf/ComplianceBF?WSDL)  \| <Anchor label=" getChangedCheckResults (JavaDoc)" target="_blank" href="https://rz3.aeb.de/test1bsm/servlet/bf/doc/ComplianceBF/de/aeb/xnsg/bsm/compliance/bf/checkrequest/IComplianceBF.html"> getChangedCheckResults (JavaDoc)</Anchor> |

The function expects the system id of the pre-system, the BSM client and an username :

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
            <resultLanguageIsoCodes>de</resultLanguageIsoCodes>
         </request>
      </urn:getCheckResult>
   </soapenv:Body>
</soapenv:Envelope>
```

The result will look simliar to the following response body:

```json
{
  "hasErrors": false,
  "hasOnlyRetryableErrors": false,
  "hasWarnings": false,
  "messages": [],
  "syncId": "353",
  "isComplete": true,
  "complianceBusinessObjects": [
    {
      "boIdClientSystem": "SAP_JNH_080_SALES_ORDER_32",
      "boIdClientSystemLabel": "SAP JNH 080 Sales order 32",
      "referenceNumber": "32",
      "orgUnitResults": [
        {
          "orgUnit": "DEFAULT",
          "resultType": "RELEASED_WITHOUT_LICENSE",
          "screeningStatus": "RELEASED_WITHOUT_LICENSE",
          "exportControlsStatus": "NOT_CHECKED",
          "lastScreeningCheck": "2026-04-29T10:19:23",
          "lastExportControlsCheck": "2026-04-29T10:19:23"
        }
      ]
    }
  ]
}
```
```xml
<?xml version="1.0" encoding="UTF-8"?>
<S:Envelope xmlns:S="http://schemas.xmlsoap.org/soap/envelope/">
    <S:Body>
        <ns2:getChangedCheckResultsResponse xmlns:ns2="urn:de.aeb.xnsg.bsm.compliance.bf.checkrequest">
            <result>
                <hasErrors>false</hasErrors>
                <hasOnlyRetryableErrors>false</hasOnlyRetryableErrors>
                <hasWarnings>false</hasWarnings>
                <syncId>353</syncId>
                <isComplete>true</isComplete>
                <complianceBusinessObjects>
                    <boIdClientSystem>SAP_JNH_080_SALES_ORDER_32</boIdClientSystem>
                    <boIdClientSystemLabel>SAP JNH 080 Sales order 32</boIdClientSystemLabel>
                    <referenceNumber>32</referenceNumber>
                    <orgUnitResults>
                        <orgUnit>DEFAULT</orgUnit>
                        <resultType>RELEASED_WITHOUT_LICENSE</resultType>
                        <screeningStatus>RELEASED_WITHOUT_LICENSE</screeningStatus>
                        <exportControlsStatus>NOT_CHECKED</exportControlsStatus>
                        <lastScreeningCheck>2026-04-29T10:19:23</lastScreeningCheck>
                        <lastExportControlsCheck>2026-04-29T10:19:23</lastExportControlsCheck>
                    </orgUnitResults>
                </complianceBusinessObjects>
            </result>
        </ns2:getChangedCheckResultsResponse>
    </S:Body>
</S:Envelope>
```

You can use the data from _complianceBusinessObjects_ to handle the changes, .e.g. update the compliance status of your business object.

Once you handled the changes you can confirm it by calling _acknowledgeChangedCheckResults_.

<br />

## acknowledgeChangedCheckResults

The function can be used to acknowledge that you handled all business object check results.

| API  | Function                                                                                                                                                                                                                                                                                                                                      |
| ---- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| REST | POST acknowledgeChangedCheckResults                                                                                                                                                                                                                                                                                                           |
| SOAP | [ComplianceBF (WSDL)](https://rz3.aeb.de/test2bsm/servlet/bf/ComplianceBF?WSDL)  \| <Anchor label=" acknowledgeChangedCheckResults (JavaDoc)" target="_blank" href="https://rz3.aeb.de/test1bsm/servlet/bf/doc/ComplianceBF/de/aeb/xnsg/bsm/compliance/bf/checkrequest/IComplianceBF.html"> acknowledgeChangedCheckResults (JavaDoc)</Anchor> |

To call the function, you need to provide the system id of the pre-system, the BSM client, a username and the _syncId_ that is provided by the response of the _getChangedCheckResults _function.

```json
{
  "clientSystemId": "BRUYES",
  "clientIdentCode": "SAP_JNH_080",
  "userName": "API_TEST",
  "resultLanguageIsoCodes": [
    "en"
  ],
  "syncId": "353"
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
           <resultLanguageIsoCodes>de</resultLanguageIsoCodes>           
					 <syncId>353</syncId>
         </request>
      </urn:getCheckResult>
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
        <ns2:acknowledgeChangedCheckResultsResponse xmlns:ns2="urn:de.aeb.xnsg.bsm.compliance.bf.checkrequest">
            <result>
                <hasErrors>false</hasErrors>
                <hasOnlyRetryableErrors>false</hasOnlyRetryableErrors>
                <hasWarnings>false</hasWarnings>
            </result>
        </ns2:acknowledgeChangedCheckResultsResponse>
    </S:Body>
</S:Envelope>
```

<br />

<br />
