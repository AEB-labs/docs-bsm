---
title: Request a Compliance Check
deprecated: false
hidden: false
metadata:
  robots: index
---
You can use the Compliance API to check a business object. This check contains compliance screening and export controls.

If you are interested in learning more about Compliance Screening or Export Controls, you can find additional information here:

* **Compliance Screening:** [https://docs.aeb.com/doc/cm-287937803-923804811-en-US/t-923804811-288463499-en-US](https://docs.aeb.com/doc/cm-287937803-923804811-en-US/t-923804811-288463499-en-US)
* **Export Controls:** [https://docs.aeb.com/doc/cm-287939723-996830731-en-US/t-996830731-288627211-en-US](https://docs.aeb.com/doc/cm-287939723-996830731-en-US/t-996830731-288627211-en-US)

<br />

To check a business object, you can use the following function:

| API  | Function                                                                                                                                                                                                                                                                                                                         |
| ---- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| REST | POST requestCheck                                                                                                                                                                                                                                                                                                                |
| SOAP | [ComplianceBF (WSDL)](https://rz3.aeb.de/test2bsm/servlet/bf/ComplianceBF?WSDL)  \| <Anchor label="requestCheck (JavaDoc)" target="_blank" href="https://rz3.aeb.de/test2bsm/servlet/bf/doc/ComplianceBF/de/aeb/xnsg/bsm/compliance/bf/checkrequest/ComplianceBusinessObjectCheckResultDTO.html">requestCheck (JavaDoc)</Anchor> |

<br />

To execute a simple check, use the request body shown below. Please ensure that the values for _businessObjectType_, _mappingProfile_, and _orgUnit_ are adjusted accordingly.

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
      "name1": "Ausländischer Kunde 50 (US)",
      "name2": "",
      "name3": "",
      "name4": "",
      "street": "Confederate Ave 15400",
      "district": "",
      "city": "Baton Rouge",
      "postalCode": "70817-3609",
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
      "name1": "Ausländischer Kunde 50 (US)",
      "name2": "",
      "name3": "",
      "name4": "",
      "street": "Confederate Ave 15400",
      "district": "",
      "city": "Baton Rouge",
      "postalCode": "70817-3609",
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
      "roleIdentCode": "PY",
      "name1": "Ausländischer Kunde 50 (US)",
      "name2": "",
      "name3": "",
      "name4": "",
      "street": "Confederate Ave 15400",
      "district": "",
      "city": "Baton Rouge",
      "postalCode": "70817-3609",
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
      "name1": "Ausländischer Kunde 50 (US)",
      "name2": "",
      "name3": "",
      "name4": "",
      "street": "Confederate Ave 15400",
      "district": "",
      "city": "Baton Rouge",
      "postalCode": "70817-3609",
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
      "name1": "DE Company Code",
      "city": "Walldorf",
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
          "name1": "Werk 1010 als Geschäftspartner",
          "name2": "",
          "name3": "",
          "name4": "",
          "street": "Dietmar-Hopp-Alle 1",
          "district": "",
          "city": "Walldorf",
          "postalCode": "69190",
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

After execution checkRequest, you'll receive the following response:

```
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

<br />
