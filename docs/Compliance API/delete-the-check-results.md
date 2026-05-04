---
title: Delete Check Results
deprecated: false
hidden: false
metadata:
  robots: index
next:
  description: >-
    In the next section, you'll learn how to handle changes of the check
    results.
  pages:
    - slug: synchronize-changed-check-results
      title: Synchronize changed check results
      type: basic
---
After performing a check request you will be able to delete the check results of a business object. Therefore, you can use the function below:

| API  | Function                                                                                                                                                                                                                                                                                      |
| ---- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| REST | POST delete                                                                                                                                                                                                                                                                                   |
| SOAP | [ComplianceBF (WSDL)](https://rz3.aeb.de/test2bsm/servlet/bf/ComplianceBF?WSDL)  \| <Anchor label=" delete (JavaDoc)" target="_blank" href="https://rz3.aeb.de/test2bsm/servlet/bf/doc/ComplianceBF/de/aeb/xnsg/bsm/compliance/bf/checkrequest/IComplianceBF.html"> delete (JavaDoc)</Anchor> |

<br />

Similiar to _Get Check Results_, the function requires the system id of the pre-system (_clientSystemid_), the BSM client (_clientIdentCode_), an username and the ID of the business object you want to delete:

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

You can validate, if the request could be executed successfully by checking if any error occured.

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
        <ns2:deleteResponse xmlns:ns2="urn:de.aeb.xnsg.bsm.compliance.bf.checkrequest">
            <result>
                <hasErrors>false</hasErrors>
                <hasOnlyRetryableErrors>false</hasOnlyRetryableErrors>
                <hasWarnings>false</hasWarnings>
            </result>
        </ns2:deleteResponse>
    </S:Body>
</S:Envelope>
```

Further details, like error messages, warnings and other informations will also be provided in the field messages:

```json
{
  "hasErrors": false,
  "hasOnlyRetryableErrors": false,
  "hasWarnings": false,
  "messages": [
    {
      "messageType": "INFO",
      "messageIdentCode": "NO_TRANSACTION_FOUND",
      "messageTexts": [
        {
          "languageISOCode": "en",
          "text": "No check transaction of client \"ATC\" with transaction number (transactionIdHost) \"SAP_JNH_080_SALES_ORDER_32$DEFAULT\" created by partner system \"PGTEST1BSM_JER\" was found."
        }
      ],
      "indentationLevel": 0
    }
  ]
}
```
```xml
<?xml version="1.0" encoding="UTF-8"?>
<S:Envelope xmlns:S="http://schemas.xmlsoap.org/soap/envelope/">
    <S:Body>
        <ns2:deleteResponse xmlns:ns2="urn:de.aeb.xnsg.bsm.compliance.bf.checkrequest">
            <result>
                <hasErrors>false</hasErrors>
                <hasOnlyRetryableErrors>false</hasOnlyRetryableErrors>
                <hasWarnings>false</hasWarnings>
                <messages>
                    <messageType>INFO</messageType>
                    <messageIdentCode>NO_TRANSACTION_FOUND</messageIdentCode>
                    <messageTexts>
                        <languageISOCode>en</languageISOCode>
                        <text>No check transaction of client "ATC" with transaction number (transactionIdHost) "SAP_JNH_080_SALES_ORDER_32$DEFAULT" created by partner system "PGTEST1BSM_JER" was found.</text>
                    </messageTexts>
                    <indentationLevel>0</indentationLevel>
                </messages>
            </result>
        </ns2:deleteResponse>
    </S:Body>
</S:Envelope>
```

<br />
