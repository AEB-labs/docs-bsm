---
title: Acknowledge changed results of EC check transactions.
excerpt: >-
  Acknowledge the changed results of EC check transactions. If calling
  *getChangedTransactions* returns false in
  *GetChangedTransactionsResponseDTO.isComplete*, there are more changed results
  available. To get those results, the already retrieved results need to be
  acknowledged with the *GetChangedTransactionsResponseDTO.syncId* from the
  *getChangedTransactions* call.
api:
  file: openapi_v3.json
  operationId: acknowledgeGetChangedTransactions
hidden: false
---