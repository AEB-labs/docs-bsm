---
title: getSupplementTaskResult
excerpt: >-
  Returns an intermediate result of calculated supplements for the provided task
  id and its current calculation state.<br> <br> Possible states of calculation
  are:<br> - INPROGRESS: entries (and ordering) might change in future calls.
  <br> - COMPLETE: ordering and entries fixed, all supplements are calculated.
  <br> <br> A new supplement task can be created by using
  createSupplementTask(CreateSupplementTaskRequestDTO).<br>
api:
  file: openapi_v3.json
  operationId: getSupplementTaskResult
hidden: false
---