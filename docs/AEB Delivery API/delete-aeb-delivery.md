---
title: Delete an AEB delivery
deprecated: false
hidden: false
metadata:
  robots: index
next:
  pages:
    - slug: copy-of-delete-aeb-delivery
      title: Get AEB Delivery
      type: basic
---
Use this API to delete an existing AEB delivery:

| Protocol | Documentation                                                                                                                                                                                                                                                                                                                                                                                         |
| -------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| REST     | <Anchor target="_blank" href="https://rz3.aeb.de/test2bsm/swagger/#/AEB%20Delivery/deleteDelivery">deleteAEBDelivery</Anchor>                                                                                                                                                                                                                                                                         |
| SOAP     | <Anchor target="_blank" href="https://rz3.aeb.de/test2bsm/servlet/bf/AEBDeliveryBF?WSDL">AEBDeliveryBF (WSDL)</Anchor> \|<br /><Anchor target="_blank" href="https://rz3.aeb.de/test2bsm/servlet/bf/doc/AEBDeliveryBF/de/aeb/xnsg/bsm/core/bf/delivery/IAEBDeliveryBF.html#deleteDelivery(de.aeb.xnsg.bsm.core.bf.delivery.delete.DeleteAEBDeliveryRequestDTO)">deleteAEBDelivery (Java Doc)</Anchor> |

This is an example for a deletion request:

```json
{
  "clientSystemId": "TEST_ID",
  "clientIdentCode": "API_TEST_CLIENT",
  "userName": "API_TEST",
  "resultLanguageIsoCodes": [
    "en"
  ],
  "boIdClientSystem": "BRUYES_1"
}
```
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:de.aeb.xnsg.bsm.core.bf.delivery">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:deleteDelivery>
         <request>
            <clientSystemId>BRUYES</clientSystemId>
            <clientIdentCode>API_CLIENT</clientIdentCode>
            <userName>SOMEONE</userName>
            <resultLanguageIsoCodes>DE</resultLanguageIsoCodes>
           <boIdClientSystem>BRUYES_1</boIdClientSystem>
         </request>
      </urn:deleteDelivery>
   </soapenv:Body>
</soapenv:Envelope>
```

In case of a successfull deletion of an AEB delivery, the response looks like this:

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
        <ns2:deleteDeliveryResponse xmlns:ns2="urn:de.aeb.xnsg.bsm.core.bf.delivery">
            <result>
                <hasErrors>false</hasErrors>
                <hasOnlyRetryableErrors>false</hasOnlyRetryableErrors>
                <hasWarnings>false</hasWarnings>
            </result>
        </ns2:deleteDeliveryResponse>
    </S:Body>
</S:Envelope>
```

If case of a an error the response looks like this:

```json
{
  "hasErrors": true,
  "hasOnlyRetryableErrors": true,
  "hasWarnings": false,
  "messages": [
    {
      "messageType": "ERROR",
      "messageIdentCode": "LOCK_ERROR",
      "messageTexts": [
        {
          "languageISOCode": "en",
          "text": "The AEB delivery could not be deleted as it is currently being processed:\r\nLocking of AEB delivery - [BRUYES_1] failed."
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
        <ns2:deleteDeliveryResponse xmlns:ns2="urn:de.aeb.xnsg.bsm.core.bf.delivery">
            <result>
                <hasErrors>true</hasErrors>
                <hasOnlyRetryableErrors>true</hasOnlyRetryableErrors>
                <hasWarnings>false</hasWarnings>
                <messages>
                    <messageType>ERROR</messageType>
                    <messageIdentCode>LOCK_ERROR</messageIdentCode>
                    <messageTexts>
                        <languageISOCode>de</languageISOCode>
                        <text>Die AEB-Lieferung konnte nicht gelöscht werden, da sie im Moment in Bearbeitung ist: &#13;
Locking für AEB-Lieferung - [BRUYES_1] fehlgeschlagen.</text>
                    </messageTexts>
                    <indentationLevel>0</indentationLevel>
                </messages>
            </result>
        </ns2:deleteDeliveryResponse>
    </S:Body>
</S:Envelope>
```
