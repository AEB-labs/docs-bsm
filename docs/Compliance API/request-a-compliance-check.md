---
title: Perform Check
deprecated: false
hidden: false
metadata:
  robots: index
next:
  description: >-
    In the next section, you'll learn how to get the check results of a business
    object.
  pages:
    - slug: get-check-result
      title: Get Check Results
      type: basic
---
You can use the Compliance API to check a business object. This check contains <Anchor label="Compliance Screening" target="_blank" href="https://docs.aeb.com/doc/cm-287937803-923804811-en-US/t-923804811-288463499-en-US">Compliance Screening</Anchor> and <Anchor label="Export Controls" target="_blank" href="https://docs.aeb.com/doc/cm-287939723-996830731-en-US/t-996830731-288627211-en-US">Export Controls</Anchor>.

To perform a check, you can use the following function:

| API  | Function                                                                                                                                                                                                                                                                                                |
| ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| REST | <Anchor label="POST requestCheck" target="_blank" href="https://rz3.aeb.de/test2bsm/swagger/">POST requestCheck</Anchor>                                                                                                                                                                                |
| SOAP | [ComplianceBF (WSDL)](https://rz3.aeb.de/test1bsm/servlet/bf/ComplianceBF?WSDL)  \| <Anchor label="requestCheck (JavaDoc)" target="_blank" href="https://rz3.aeb.de/test2bsm/servlet/bf/doc/ComplianceBF/de/aeb/xnsg/bsm/compliance/bf/checkrequest/IComplianceBF.html">requestCheck (JavaDoc)</Anchor> |

<br />

To execute a check, use the request body below and adapt the fields _businessObjectType_, _mappingProfile_, and _orgUnits_ to match your specific use case.

```json JSON
{
  "boIdClientSystem": "SAP_JNH_080_SALES_ORDER_1",
  "boIdClientSystemLabel": "SAP JNH 080 Sales order 1",
  "referenceNumber": "1",
  "businessObjectType": "SAP_SALES_ORDER",
  "businessObjectSubType": "OR",
  "mappingProfile": "SAP",
  "parties": [
    {
      "orgUnits": [
        "SalesOrganization1010"
      ],
      "roleIdentCode": "SP",
      "name1": "ACME Inc.",
      "name2": "",
      "name3": "",
      "name4": "",
      "street": "Confederate Ave 15400",
      "district": "",
      "city": "Baton Rouge",
      "postalCode": "70817",
      "countryIso": "US",
      "poBox": "",
      "postalCodePoBox": "",
      "companyReference": "10100050",
      "addressType": "2",
      "telephoneNo": "+19992365237",
      "email": "info@10100050.com",
      "ids": []
    },
    {
      "orgUnits": [
        "SalesOrganization1010"
      ],
      "roleIdentCode": "BP",
      "name1": "ACME Inc.",
      "name2": "",
      "name3": "",
      "name4": "",
      "street": "Confederate Ave 15400",
      "district": "",
      "city": "Baton Rouge",
      "postalCode": "708179",
      "countryIso": "US",
      "poBox": "",
      "postalCodePoBox": "",
      "companyReference": "10100050",
      "addressType": "2",
      "telephoneNo": "+19992365237",
      "email": "info@10100050.com",
      "ids": []
    },
    {
      "orgUnits": [
        "SalesOrganization1010"
      ],
      "roleIdentCode": "SH",
      "name1": "ACME Fullfillment Corp",
      "name2": "",
      "name3": "",
      "name4": "",
      "street": "Main Road 123",
      "district": "",
      "city": "Mt. Laurel",
      "postalCode": "20912",
      "countryIso": "US",
      "poBox": "",
      "postalCodePoBox": "",
      "companyReference": "10100050",
      "addressType": "2",
      "telephoneNo": "+19992365237",
      "email": "info@10100050.com",
      "ids": []
    },
    {
      "orgUnits": [
        "CompanyCode1010",
        "SalesOrganization1010"
      ],
      "roleIdentCode": "SalesOrganization",
      "name1": "BEA AG",
      "city": "Stuttgart",
      "countryIso": "DE",
      "companyReference": "1010"
    }
  ],
  "items": [
    {
      "orderNumber": "1",
      "idClientSystem": "10",
      "idClientSystemLabel": "FIN111, MTS-DI, PD",
      "orgUnits": [
        "ProductionPlant1010"
      ],
      "materialNo": "FG111",
      "quantity": {
        "value": 2,
        "unit": "PCE"
      },
      "values": [
        {
          "value": 0.00,
          "currencyIso": "USD"
        }
      ],
      "parties": [
        {
          "orgUnits": [
            "SalesOrganization1010",
            "ProductionPlant1010"
          ],
          "roleIdentCode": "ProductionPlant",
          "name1": "BEA Logistics AG",
          "name2": "",
          "name3": "",
          "name4": "",
          "street": "Peter-Michael-Belz-Allee 1",
          "district": "",
          "city": "Stuttgart",
          "postalCode": "70567",
          "countryIso": "DE",
          "poBox": "",
          "postalCodePoBox": "",
          "companyReference": "1010",
          "addressType": "2",
          "telephoneNo": "+4999907770",
          "email": "info@10401010.com",
          "ids": [
            {
              "idType": "DE0",
              "idValue": "DE154512324"
            }
          ]
        }
      ],
      "decisiveDate": "2024-06-13",
      "ctryProductOrigin": ""
    }
  ],
  "monitorParty": {
    "roleIdentCode": "SH",
    "companyReference": "10100050"
  },
  "forceCheck": false,
  "clientSystemId": "SAP_JNH_080",
  "clientIdentCode": "API_TEST_CLIENT",
  "userName": "API_TEST",
  "resultLanguageIsoCodes": [
    "EN"
  ]
}
```
```xml XML
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:de.aeb.xnsg.bsm.compliance.bf.checkrequest">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:requestCheck>
         <request>
            <clientSystemId>BRUYES</clientSystemId>
            <clientIdentCode>API_TEST_CLIENT</clientIdentCode>
            <userName>API_TEST</userName>
            <resultLanguageIsoCodes>EN</resultLanguageIsoCodes>
            <boIdClientSystem>UNIQUE_BO_ID</boIdClientSystem>
            <boIdClientSystemLabel>UNIQUE_BO_ID_READBLE</boIdClientSystemLabel>
            <referenceNumber>REFERENCE_NUMBER</referenceNumber>
            <businessObjectType>BUSINESS_OBJECT_TYPE</businessObjectType>
            <mappingProfile>CMP_MAPPING_PROFILE</mappingProfile>
            <parties>
               <orgUnits>ORG_UNIT</orgUnits>
               <roleIdentCode></roleIdentCode>
               <name1>United Aircraft Corporation</name1>
               <street>Ulansky side-street 22</street>
               <city>Moscow</city>
               <postalCode>101000</postalCode>
               <countryIso>RU</countryIso>
               <companyReference>United_Aircraft_Corporation</companyReference>
            </parties>
           <monitorParty>
             <roleIdentCode></roleIdentCode>
             <companyReference>United_Aircraft_Corporation</companyReference>
           </monitorParty>
           <forceCheck>false</forceCheck>
         </request>
      </urn:requestCheck>
   </soapenv:Body>
</soapenv:Envelope>
```

<br />

You'll receive a response similar to the example shown below:

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

The response body includes the compliance status, the screening status, and the export controls status for each org unit. If you have performed an export controls check, the response will additionally contain the check result for each item.

<br />
