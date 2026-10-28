---
title: Origin & Preference
deprecated: false
hidden: false
metadata:
  robots: index
---
Configure the custom HTTP service in the **Origin & Preferences collector profile**. BSM calls it after collecting a business object from SAP and before forwarding its update or deletion.

The concrete request type depends on the business object. Supported examples include addresses, materials, bills of material, and purchase orders. Generate the handler template for the request type used by your profile; one handler body must not assume that every Origin & Preferences request is a material.

For a **material** request, the following example adds a suffix to its English description:

```abap
METHOD after_std_filling.
  LOOP AT ch_object-descriptions
       ASSIGNING FIELD-SYMBOL(<description>).
    IF <description>-language = 'EN'.
      <description>-description =
        |{ <description>-description } (SAP)|.
    ENDIF.
  ENDLOOP.
ENDMETHOD.
```

This example is specific to the material request structure. Keep the remaining request fields unchanged, especially its business-object ID and deletion flag. Return the complete, unchanged request when no customization is required.

**Clearing&#x20;**`ch_object`**&#x20;skip processing the business object.**&#x20;
