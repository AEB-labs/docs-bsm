---
title: Set up a custom HTTP service
deprecated: false
hidden: false
metadata:
  robots: index
---
Use this setup for the custom APIs described in the business-area guides. The request and response types depend on the hook.

## Create the service in ADT

1. Connect your SAP cloud system to ABAP Development Tools (ADT) and create or select a package.
2. Create an inbound **HTTP Service** (`New` → `Other` → `HTTP Service`).
3. Create a **Communication Scenario** (`New` → `Other` → `Communication Scenario`). On its **Inbound** tab, add the HTTP service.
4. Publish the communication scenario locally and create a communication arrangement that permits the BSM communication user to call the service.

## Add the handler

Use the code template provided in the relevant BSM profile and insert it into your HTTP service class. The generated wrapper reads the JSON request, calls your handler method, and serializes its result. Implement your business-specific change inside that method rather than changing the generated request and response structures by hand.

For a request-modifying hook, the handler changes `ch_object`:

```abap
METHOD after_std_filling.
  "Change ch_object here when your business rule applies.
ENDMETHOD.
```

A classification-value synchronization hook instead receives `im_request` and returns `ch_response`. See [Customize product classification](/docs/customize-product-classification) for its response and retry behavior.

Enter the HTTP service name in the appropriate collector or check profile. Generate the template for **that hook and its current request type**: the structures are not interchangeable between business areas.

> Return the complete request object for request-modifying hooks. Do not construct a partial response containing only changed fields. Test the service with non-production data before enabling it in a productive profile.
