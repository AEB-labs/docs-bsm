---
title: Compliance
deprecated: false
hidden: false
metadata:
  robots: index
---
Configure the custom HTTP service in the **general compliance check profile** for the relevant SAP business-object type. BSM calls it after collecting the check request and before submitting the request to the compliance engine.

The service receives a `ComplianceBusinessObjectCheckRequestDTO` and returns the same type. The following example selects a different mapping profile for one illustrative reference number:

```abap
METHOD after_std_filling.
  IF ch_object-reference_number = '12345'.
    ch_object-mapping_profile = 'AEB_TEST_PROFILE'.
  ENDIF.
ENDMETHOD.
```

Replace the example values with your own rule and an existing mapping profile. For other references, the request remains unchanged.

This hook modifies the **check request**. It does not return the result of the compliance check. Check-result errors and retries are handled later, after the compliance engine has been called.
