---
title: Carrier API Gateway - Overview
deprecated: false
hidden: false
metadata:
  robots: index
next:
  pages:
    - slug: determine-freight-costs
      title: 'Determine freight costs for completed shipping orders  '
      type: basic
    - slug: request-quotes
      title: 'Request quotes '
      type: basic
---
## Functional overview

With this function, you can determine freight costs based on your customer-specific freight agreements. This gives you cost transparency and enables you to make well-founded shipping decisions – both in the actual shipping process and in upstream process steps.  The API provides two central features:

* Determination of freight costs for already completed shipping orders - see [Determine freight costs](https://aeb-bsm.readme.io/docs/determine-freight-costs)
* Rate shopping - see [Request quotes](https://aeb-bsm.readme.io/docs/request-quotes)

<br />

## WSDL

The WSDL file can be downloaded here: <Anchor label="WSDL" target="_blank" href="https://rz3.aeb.de/test1bsm/servlet/bf/BSMCarrierBF?WSDL">WSDL</Anchor>

<br />

## Legal disclaimers for using the API

All API responses include important notices stating that freight costs and transit times may not be used for comparison with other service providers. This is a legal requirement for usage.

AEB refers to the clearly formulated information in the service descriptions and notes in the API responses. The responsibility for compliance with carrier conditions lies with the customer. Individual customer solutions are outside of AEB responsibility.

Only customer-specific freight agreements with the respective transport service provider are taken into account.
Freight Cost Determination is only available for transport service providers which provide an API for querying freight costs. 
The scope, completeness, and accuracy of the freight cost data provided as part of freight cost determination are solely dependent on the information provided by the respective transport service provider via its interfaces.
The freight costs determined via the API of the transport service providers do not constitute a binding price commitment and may differ from the freight costs actually invoiced by the transport service provider. Deviations may arise in particular due to value-added services, subsequent service changes, carrier-specific billing logic, or incomplete or deviating shipment data.
Only the settlements and invoices issued by the respective transport service provider are binding for invoicing.

AEB assumes no responsibility and no liability for the completeness, correctness, timeliness, or accuracy of the freight cost data provided within the scope of Freight Cost Determination.