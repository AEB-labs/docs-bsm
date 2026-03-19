---
title: createSupplementTask
excerpt: >-
  Creates a new supplement task and returns a unique task id.<br> <br>In case of
  successful creation, the response will contain the unique taskId of the
  created supplement task. The respective supplement task can be found by this
  task id. Supplement calculation starts in an asynchronous process. The current
  state of calculation can be request by handing over the provided task id via
  the call of getSupplementTaskResult(GetSupplementTaskResultRequestDTO).<br>
api:
  file: openapi_v3.json
  operationId: createSupplementTask
hidden: false
---