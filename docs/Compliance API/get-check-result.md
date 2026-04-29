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

```
```

<br />
