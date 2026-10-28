---
title: Product Classification
deprecated: false
hidden: false
metadata:
  robots: index
---
The **classification collector profile** supports two different custom HTTP services. Configure the service corresponding to the behavior you need.

## Modify material data after standard filling

This hook receives an `UpdateMaterialRequestDTO` after the standard material data has been filled and before the material is updated. Return the complete, possibly modified request.

The following example adds a suffix to the English material description:

```abap
METHOD after_std_filling.
  LOOP AT ch_object-material_data-material_descriptions
       ASSIGNING FIELD-SYMBOL(<description>).
    IF <description>-language = 'en'.
      <description>-description =
        |{ <description>-description } (SAP)|.
    ENDIF.
  ENDLOOP.
ENDMETHOD.
```

Adapt the condition and text to your requirements. **Only return an empty request as a way to skip the update or to delete the material if it exists.**

## Synchronize classification values

The classification-value service receives an event, for example:

```json
{
  "material_number": "MAT-1",
  "type_name": "DE_EXPORT_CONTROL",
  "valid_from": "2025-01-01",
  "value": "0001",
  "event_type": "UPDATE"
}
```

The service must return a processing response, **not** the event request. Use the generated request/response handler; unlike `after_std_filling`, it has an input request and a separate output response.

The following _demonstration_ shows the three response outcomes. Replace the illustrative material-number checks with actual SAP update logic: report success only after the event was processed successfully.

```abap
METHOD handle_cls_value.
  CLEAR ch_response.

  IF im_request-material_number = 'RETRY-DEMO'.
    ch_response-has_errors = 'X'.
    ch_response-has_only_retryable_errors = 'X'.
    RETURN.
  ENDIF.

  IF im_request-material_number = 'FAIL-DEMO'.
    ch_response-has_errors = 'X'.
    ch_response-has_only_retryable_errors = space.
    RETURN.
  ENDIF.

  "Perform the SAP update before reporting success.
  ch_response-has_errors = space.
  ch_response-has_only_retryable_errors = space.
ENDMETHOD.
```

| Response                                              | Meaning in BSM                                             |
| ----------------------------------------------------- | ---------------------------------------------------------- |
| `has_errors` blank                                    | Processing succeeded.                                      |
| `has_errors = 'X'`, `has_only_retryable_errors = 'X'` | Temporary failure; BSM invokes its retry strategy.         |
| `has_errors = 'X'`, `has_only_retryable_errors` blank | Permanent failure; BSM logs the error without retrying it. |

## Response messages

The response can contain `messages` with one of these `message_type` values:

| `message_type` | Meaning               |
| -------------- | --------------------- |
| `ERROR`        | Error message         |
| `WARNING`      | Warning message       |
| `INFO`         | Informational message |

For example, a successful synchronization can include a warning:

```json
{
  "has_errors": " ",
  "has_only_retryable_errors": " ",
  "messages": [
    {
      "message_type": "WARNING",
      "message_ident_code": "CLS_WARNING",
      "indentation_level": 0,
      "message_texts": [
        {
          "language_i_s_o_code": "en",
          "text": "The classification value was synchronized with a warning."
        }
      ]
    }
  ]
}
```

The `message_ident_code` is optional; use `message_texts` for localized details. The generated ABAP response type contains a `messages` table. **Message severity does not control retry behavior:** BSM determines success, permanent failure, or retry from `has_errors` and `has_only_retryable_errors`. For a retryable failure, set both flags; for a permanent failure, set only `has_errors`.

> A `DELETE` event must be handled according to your SAP-side synchronization rule.&#x20;
