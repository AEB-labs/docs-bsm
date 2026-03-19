---
title: Get changed material master data
deprecated: false
hidden: false
metadata:
  robots: index
next:
  description: 'Now you can try to get an declaration of origin. '
  pages:
    - slug: declaration-of-origin
      title: Declaration of origin
      type: basic
---
If you like to synchronize the material master data e.g. to persist the data in the erp system you should use our getChangedMaterialMasterData-API. The logic of your program could look like this:

* call getChangedMaterialMasterData 
* persist the data of the response
* check if the isComplete-Flag is true
* if yes call acknowledgeGetChangedMaterialMasterData with the syncId given in getChangedMaterialMasterData
* If no call getChangedMaterialMasterData again

Ok and now let's do that in detail with some sample calls. So as i sad first we call getChangedMaterialMasterData.

```json
`{
  "clientSystemId": "ERP_SYSTEM_ID",
  "clientIdentCode": "AEB_TEST_CLIENT",
  "userName": "user",
  "resultLanguageIsoCodes": [
    "en"
  ]
}
```



The answer of this call could then look like this.

```json
`{
  "hasErrors": false,
  "hasOnlyRetryableErrors": false,
  "hasWarnings": false,
  "messages": [],
  "syncId": "8",
  "isComplete": true,
  "materialMasterData": [
    {
      "materialNo": "MAT",
      "orderItemReference": "4711_10",
      "destinationCountry": "US",
      "sourceCountry1": "CE",
      "sourceCountry2": "CH",
      "commodityCode1": "010121051",
      "minimumSalesValue": 999999999,
      "cummulationType": "1",
      "currency": "EUR",
      "isLogicalDeleted": false
    },
    {
      "materialNo": "MAT",
      "orderItemReference": "4711_10",
      "destinationCountry": "DE",
      "sourceCountry1": "CE",
      "sourceCountry2": "CH",
      "commodityCode1": "010121051",
      "minimumSalesValue": 999999999,
      "cummulationType": "2",
      "currency": "EUR",
      "isLogicalDeleted": false
    }
  ]
}
```

<br />

As you can see the isComplete is set to true and the syncId is 8. So let's do the acknowledge-API call.

```json
`{
  "clientSystemId": "E01_400",
  "clientIdentCode": "AEB_TEST_CLIENT",
  "userName": "user",
  "syncId" : 8,
  "resultLanguageIsoCodes": [
    "en",
    "de"
  ]
}

```

If you now call the getChangedMaterialMasterData-API again no data will return. 

<br />
