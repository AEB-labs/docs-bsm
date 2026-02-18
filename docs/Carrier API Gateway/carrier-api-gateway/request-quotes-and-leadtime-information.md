---
title: Request quotes and leadtime information
excerpt: >-
  The service "Carrier Information API Gateway" provides carrier related
  information, e.g. runtimes and freight charges. 
deprecated: false
hidden: false
metadata:
  robots: index
---
## getQuotes API

With the getQuotes API call, you can retrieve quotes for freight charges and lead times based on the data sent in the request. Unlike the getShipment API, this call does not require an existing shipping order in Carrier Connect.

The API expects two parameters in the request:

* Shipment -  shipping data to request a quote, see list of fields [here](https://rz3.aeb.de/test1bsm/servlet/bf/doc/DLCarrierBF/de/aeb/xnsg/dl/bf/DLShipmentRequestDataDTO.html)
* ShippingTime  - the expected time of shipping, in format HH:MM:SS

Example call:

```xml XML
<SHIPMENT>
        <CARRIERIDENTCODE>UPS</CARRIERIDENTCODE>
        <CONSIGNEE>
          <INITFROMCOMPANYMASTERFILEDATA>false</INITFROMCOMPANYMASTERFILEDATA>
          <COMPANYNUMBER>1200</COMPANYNUMBER>
          <CITY>Hamburg</CITY>
          <COUNTRYISOCODE>DE</COUNTRYISOCODE>
          <EMAILADDRESS>info@acme.com</EMAILADDRESS>
          <NAME>Elblogistik Services</NAME>
          <POSTCODE>54001</POSTCODE>
          <STREET>Hafenstrasse 678</STREET>
        </CONSIGNEE>
        <CONTENTS>Electronic parts</CONTENTS>
        <INCOTERMDESTINATION>Stuttgart</INCOTERMDESTINATION>
        <INVOICEVALUE>
          <CURRENCYISO>EUR</CURRENCYISO>
          <VALUE>2222.00</VALUE>
        </INVOICEVALUE>
        <ISDOCUMENTSHIPMENT>false</ISDOCUMENTSHIPMENT>
        <ITEMS>
          <COUNTRYOFORIGINSISOCODE>DE</COUNTRYOFORIGINSISOCODE>
          <CUSTOMSTARIFFNUMBER>81022941</CUSTOMSTARIFFNUMBER>
          <CUSTOMSVALUE>
            <CURRENCYISO>EUR</CURRENCYISO>
            <VALUE>2222.00</VALUE>
          </CUSTOMSVALUE>
          <DESCRIPTION>LCD Monitor</DESCRIPTION>
          <GOODSVALUE>
            <CURRENCYISO>EUR</CURRENCYISO>
            <VALUE>2222.00</VALUE>
          </GOODSVALUE>
          <ITEMTRANSACTIONID>0080000584_000010</ITEMTRANSACTIONID>
          <NETWEIGHT>
            <UNIT>KG</UNIT>
            <VALUE>16.200</VALUE>
          </NETWEIGHT>
          <GROSSWEIGHT>
            <UNIT>KG</UNIT>
            <VALUE>18.000</VALUE>
          </GROSSWEIGHT>
          <QUANTITY>
            <UNIT>ST</UNIT>
            <VALUE>1.000</VALUE>
          </QUANTITY>
          <REFERENCENUMBER1>10</REFERENCENUMBER1>
        </ITEMS>
        <PACKAGES>
          <CONTAINEDITEMS>
            <ITEMTRANSACTIONID>0080000584_000010</ITEMTRANSACTIONID>
            <QUANTITYVALUE>1.000</QUANTITYVALUE>
          </CONTAINEDITEMS>
          <DIMENSIONS>
            <IDENTCODE>CM</IDENTCODE>
            <HEIGHT>100.00</HEIGHT>
            <LENGTH>60.00</LENGTH>
            <WIDTH>30.00</WIDTH>
          </DIMENSIONS>
          <GROSSWEIGHT>
            <UNIT>KG</UNIT>
            <VALUE>25.000</VALUE>
          </GROSSWEIGHT>
          <PACKAGETYPEIDENTCODE>CT</PACKAGETYPEIDENTCODE>
          <REFERENCENUMBER1>300001500</REFERENCENUMBER1>
          <PACKAGETRANSACTIONID>0000000642</PACKAGETRANSACTIONID>
        </PACKAGES>
        <REFERENCENUMBER1>80000584</REFERENCENUMBER1>
        <SHIPPINGDATE>2026-02-16</SHIPPINGDATE>
        <SHIPPINGPT>
          <COMPANYNUMBER>1010</COMPANYNUMBER>
          <CITY>Stuttgart</CITY>
          <COUNTRYISOCODE>DE</COUNTRYISOCODE>
          <COUNTY>BW</COUNTY>
          <EMAILADDRESS>info@shipper.com</EMAILADDRESS>
          <NAME>Shipping Point 1010 DE</NAME>
          <POSTCODE>70567</POSTCODE>
          <STREET>Sigmaringerstr. 109</STREET>
        </SHIPPINGPT>
        <TERMSOFDELIVERYCODE>FCA</TERMSOFDELIVERYCODE>
        <TRANSACTIONID>S01     400008000058420260216092737JLF  1010</TRANSACTIONID>
        <TRANSACTIONLABEL>80000584</TRANSACTIONLABEL>
        <ORGANIZATIONUNITCLIENTSYSTEM>7000</ORGANIZATIONUNITCLIENTSYSTEM>        
</SHIPMENT>
<SHIPPINGTIME>18:30:00</SHIPPINGTIME>      
```

<br />

<br />

<br />
