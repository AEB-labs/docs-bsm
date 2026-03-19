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
* If no call getChangedMaterialMasterData with the syncId give in the last call of getChangedMaterialMasterData

Ok and now let's do that in detail with some sample calls. So as i said first we call getChangedMaterialMasterData.

<br />

<br />
