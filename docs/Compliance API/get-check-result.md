---
title: Get Check Results
deprecated: false
hidden: false
metadata:
  robots: index
next:
  description: >-
    In the next section, you'll learn how to delete the check results of a
    business object.
  pages:
    - slug: delete-the-check-results
      title: Delete the Check Results
      type: basic
---
You can fetch the check results of a business object by executing the following function:

| API  | Function                                                                                                                                                                                                                                                                                                      |
| ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| REST | POST getCheckResult                                                                                                                                                                                                                                                                                           |
| SOAP | [ComplianceBF (WSDL)](https://rz3.aeb.de/test2bsm/servlet/bf/ComplianceBF?WSDL)  \| <Anchor label=" getCheckResult (JavaDoc)" target="_blank" href="https://rz3.aeb.de/test1bsm/servlet/bf/doc/ComplianceBF/de/aeb/xnsg/bsm/compliance/bf/checkrequest/IComplianceBF.html"> getCheckResult (JavaDoc)</Anchor> |

<br />

To execute the function, you' have to provide the system id of the pre-system (_clientSystemid_), the BSM client (_clientIdentCode_), an username and the ID of the business object you want to fetch:

```json
{
  "clientSystemId": "BRUYES",
  "clientIdentCode": "SAP_JNH_080",
  "userName": "API_TEST",
  "resultLanguageIsoCodes": [
    "en"
  ],
  "boIdClientSystem": "SAP_JNH_080_SALES_ORDER_1"  
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
            <boIdClientSystem>SAP_JNH_080_SALES_ORDER_1</boIdClientSystem>
         </request>
      </urn:getCheckResult>
   </soapenv:Body>
</soapenv:Envelope>
```

The response is equal to the _requestCheck_ response. It includes the compliance status, the screening status and the export controls status for each org unit and for each item.

```json
{
  "hasErrors": false,
  "hasOnlyRetryableErrors": false,
  "hasWarnings": false,
  "messages": [],
  "boIdClientSystem": "SAP_JNH_080_SALES_ORDER_1",
  "boIdClientSystemLabel": "SAP JNH 080 Sales order 1",
  "referenceNumber": "1",
  "orgUnitResults": [
    {
      "orgUnit": "DEFAULT",
      "resultType": "NOT_CRITICAL",
      "screeningStatus": "NOT_CRITICAL",
      "exportControlsStatus": "NOT_CRITICAL",
      "lastScreeningCheck": "2026-04-27T10:08:45",
      "lastExportControlsCheck": "2026-04-27T10:08:45"
    }
  ],
  "items": [
    {
      "idClientSystem": "10",
      "orgUnitResults": [
        {
          "orgUnit": "DEFAULT",
          "resultType": "NOT_CRITICAL"
        }
      ]
    }
  ],
  "blockMemories": []
}
```
```xml
<?xml version="1.0" encoding="UTF-8"?>
<S:Envelope xmlns:S="http://schemas.xmlsoap.org/soap/envelope/">
    <S:Body>
        <ns2:requestCheckResponse xmlns:ns2="urn:de.aeb.xnsg.bsm.compliance.bf.checkrequest">
            <result>
                <hasErrors>false</hasErrors>
                <hasOnlyRetryableErrors>false</hasOnlyRetryableErrors>
                <hasWarnings>false</hasWarnings>
                <boIdClientSystem>SAP_JNH_080_SALES_ORDER_1</boIdClientSystem>
                <boIdClientSystemLabel>SAP JNH 080 Sales order 1</boIdClientSystemLabel>
                <referenceNumber>1</referenceNumber>
                <orgUnitResults>
                    <orgUnit>DEFAULT</orgUnit>
                    <resultType>NOT_CRITICAL</resultType>
                    <screeningStatus>NOT_CRITICAL</screeningStatus>
                    <exportControlsStatus>NOT_CRITICAL</exportControlsStatus>
                    <lastScreeningCheck>2026-04-27T10:45:00</lastScreeningCheck>
                    <lastExportControlsCheck>2026-04-27T10:45:00</lastExportControlsCheck>
                </orgUnitResults>
                <items>
                    <idClientSystem>10</idClientSystem>
                    <orgUnitResults>
                        <orgUnit>DEFAULT</orgUnit>
                        <resultType>NOT_CRITICAL</resultType>
                    </orgUnitResults>
                </items>
            </result>
        </ns2:requestCheckResponse>
    </S:Body>
</S:Envelope>
```

<br />
