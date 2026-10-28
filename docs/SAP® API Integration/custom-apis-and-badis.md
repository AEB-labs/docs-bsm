---
title: Custom APIs and BAdIs
deprecated: false
hidden: false
metadata:
  robots: index
---
SAP® API Integration can call a custom HTTP service to adapt data collected from SAP before it going on in processing in BSM or an AEB business service. The HTTP service is configured in the relevant collector or check profile.

There are two kinds of hooks:

- **Modify a request:** The service receives a request, changes it if necessary, and returns the request. This is for example used for AEB Deliveries, Compliance checks, classification material data, and Origin & Preferences data.
- **Handle an event:** The service receives a classification-value event and returns a processing result. This is used to synchronize classification values back to SAP.

| Business area          | Hook                                        | Configuration                          |
| ---------------------- | ------------------------------------------- | -------------------------------------- |
| AEB Delivery           | Modify the collected delivery               | AEB delivery collector profile         |
| Trade Compliance       | Modify a check request                      | General check profile                  |
| Product Classification | Modify material data after standard filling | Classification collector profile       |
| Product Classification | Synchronize a classification value          | Classification collector profile       |
| Origin & Preferences   | Modify a collected business object          | Origin & Preferences collector profile |

Start with [Set up a custom HTTP service](https://aeb-bsm.readme.io/docs/set-up-a-custom-http-service), then follow the guide for your business area:

- [AEB Delivery](https://aeb-bsm.readme.io/docs/aeb-delivery)
- [Compliance](https://aeb-bsm.readme.io/docs/compliance)
- [Product Classification](https://aeb-bsm.readme.io/docs/product-classification)
- [Origin & Preference](https://aeb-bsm.readme.io/docs/origin-preference)

> The configured **HTTP service name** determines which SAP service BSM calls. The API handler setting supports the SAP-side implementation and code generation; it does not select the service at runtime.