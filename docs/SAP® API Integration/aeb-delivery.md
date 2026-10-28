---
title: AEB Delivery
deprecated: false
hidden: false
metadata:
  robots: index
---
#

Configure the custom HTTP service in the **AEB delivery collector profile**. BSM calls it after collecting the delivery from SAP and before updating the AEB delivery.

The service receives an `UpdateAEBDeliveryRequestDTO` and must return an `UpdateAEBDeliveryRequestDTO`. You can modify the collected request, including delivery data and transfer options, while retaining the other fields.

For example, the following handler disables label printing for one illustrative client:

```abap
METHOD after_std_filling.
  IF ch_object-client_ident_code = 'DEMO'.
    ch_object-print_labels = space.
  ENDIF.
ENDMETHOD.
```

Replace `DEMO` with a condition appropriate to your installation. Generate the handler template from the collector profile so that `ch_object` has the correct structure.

If the service returns no request, BSM stops processing this delivery; it does not send an empty delivery. Errors from the custom service also stop this update. Consequently, return the unchanged request when no customization is required.
