---
title: Custom APIs and BAdIs
deprecated: false
hidden: false
metadata:
  robots: index
---
SAP® API Integration can call a custom HTTP service to adapt data collected from SAP before it is sent to BSM or an AEB business service. The HTTP service is configured in the relevant collector or check profile.

There are two kinds of hooks:

- **Modify a request:** The service receives a request, changes it if necessary, and returns the request. This is used for deliveries, compliance checks, classification material data, and Origin & Preferences data.
- **Handle an event:** The service receives a classification-value event and returns a processing result. This is used to synchronize classification values back to SAP.

| Business area          | Hook                                        | Configuration                          |
| ---------------------- | ------------------------------------------- | -------------------------------------- |
| AEB Delivery           | Modify the collected delivery               | AEB delivery collector profile         |
| Trade Compliance       | Modify a check request                      | General check profile                  |
| Product Classification | Modify material data after standard filling | Classification collector profile       |
| Product Classification | Synchronize a classification value          | Classification collector profile       |
| Origin & Preferences   | Modify a collected business object          | Origin & Preferences collector profile |

Start with [Set up a custom HTTP service](/docs/set-up-a-custom-http-service), then follow the guide for your business area:

- [Customize AEB deliveries](/docs/customize-aeb-deliveries)
- [Customize trade compliance checks](/docs/customize-trade-compliance-checks)
- [Customize product classification](/docs/customize-product-classification)
- [Customize Origin & Preferences data](/docs/customize-origin-and-preferences-data)

> The configured **HTTP service name** determines which SAP service BSM calls. The API handler setting supports the SAP-side implementation and code generation; it does not select the service at runtime.
