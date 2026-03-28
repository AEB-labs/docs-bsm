---
title: Exchange Data
deprecated: false
hidden: false
icon: far fa-house-medical
metadata:
  robots: index
---
There are two usecases where data between Customs Management and other business services has to be exchanged:

* Paperless Trade in context of Carrier Connect
* Approvals in context of Export Controls

For those usecases the Business Service Managment offers an extended createConsignment-API.

The API is extended by information about the transaction of the processed mentioned before.

There are two usecase-Ids:

* EC_APPROVAL_DATA for data exchange in context of Export Controls approvals
* CCO_SHP_CUSTOMS_UPD for data exchange in context of Carrier Connect and Paperless Trade

The CreateShipment-API call could the look like the following.

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:de.aeb.xnsg.bsm.customs.bf">
    <soapenv:Header/>
    <soapenv:Body>
        <urn:createConsignment>
            <!--Optional:-->
            <requestDTO>
                <clientSystemId>SAP_E01</clientSystemId>
                <clientIdentCode>API_TEST_CLIENT</clientIdentCode>
                <userName>USER</userName>
                <resultLanguageIsoCodes>EN</resultLanguageIsoCodes>
                <bsmConsignment>
                    <interactionControls>
                        <usecase>
                            <usecaseId>CCO_SHP_CUSTOMS_UPD</usecaseId>
                        </usecase>
                        <ids>
                            <boIdClientSystem>SAP_E01_800_BILLING_DOC_90000001</boIdClientSystem>
                            <clientSystemId>SAP_E01</clientSystemId>
                        </ids>
                    </interactionControls>
                    <consignmentIdClientSystem>SAP_E01_800_BILLING_DOC_90000001</consignmentIdClientSystem>
                    <organizationUnitClientSystem>DEFAULT</organizationUnitClientSystem>
                    <consignmentNumber>90000001</consignmentNumber>
                    <profileCode>INVOICE_STD</profileCode>
                    <personInCharge>
                        <forename>Jan</forename>
                        <surname>Ambrosch</surname>
                    </personInCharge>
                    <bsmDeliveries>
                        <deliveryIdClientSystem>SAP_E01_800_BILLING_DOC_90000001</deliveryIdClientSystem>
                        <organizationUnitClientSystem>DEFAULT</organizationUnitClientSystem>
                        <deliveryNumber>90000001</deliveryNumber>
                        <remark>90000001</remark>
                        <dispatchCountryCode>DE</dispatchCountryCode>
                        <destinationCountryCode>US</destinationCountryCode>
                        <decisiveDate>
                            <dateInTimezone>2026-01-20 00:00:00</dateInTimezone>
                            <timezone>CET</timezone>
                        </decisiveDate>
                        <tradeTerms>
                            <incotermCode>EXW</incotermCode>
                            <place>Walldorf</place>
                        </tradeTerms>
                        <clientSpecificFields/>
                        <parties>
                            <partyType>SHIPPING_POINT</partyType>
                            <companyNumber>1010</companyNumber>
                            <street>Dietmar-Hopp-Allee</street>
                            <city>Walldorf</city>
                            <postCode>69190</postCode>
                            <country>DE</country>
                            <countryRegionCode>BW</countryRegionCode>
                        </parties>
                        <parties>
                            <partyType>DECLARANT</partyType>
                            <companyNumber>1010</companyNumber>
                            <name>DE Company Code</name>
                            <city>Walldorf</city>
                            <country>DE</country>
                        </parties>
                        <parties>
                            <partyType>EXPORTER</partyType>
                            <companyNumber>1010</companyNumber>
                            <name>DE Company Code</name>
                            <city>Walldorf</city>
                            <country>DE</country>
                        </parties>
                        <parties>
                            <partyType>BUYER</partyType>
                            <companyNumber>10100050</companyNumber>
                            <name>Ausländischer Kunde 50 (US)</name>
                            <street>Confederate Ave 15400</street>
                            <city>Baton Rouge</city>
                            <postCode>70817-3609</postCode>
                            <country>US</country>
                        </parties>
                        <parties>
                            <partyType>CONSIGNOR</partyType>
                            <companyNumber>1010</companyNumber>
                            <street>Dietmar-Hopp-Allee</street>
                            <city>Walldorf</city>
                            <postCode>69190</postCode>
                            <country>DE</country>
                            <countryRegionCode>BW</countryRegionCode>
                        </parties>
                        <parties>
                            <partyType>CONSIGNEE</partyType>
                            <companyNumber>10100050</companyNumber>
                            <name>Ausländischer Kunde 50 (US)</name>
                            <street>Confederate Ave 15400</street>
                            <city>Baton Rouge</city>
                            <postCode>70817-3609</postCode>
                            <country>US</country>
                        </parties>
                        <parties>
                            <partyType>SELLER</partyType>
                            <companyNumber>1010</companyNumber>
                            <city>Walldorf</city>
                            <country>DE</country>
                        </parties>
                        <invoices>
                            <invoiceIdClientSystem>SAP_JNH_080_BILLING_DOC_90000037</invoiceIdClientSystem>
                            <invoiceNumber>90000037</invoiceNumber>
                            <invoiceDate>
                                <dateInTimezone>2026-01-20 01:00:00</dateInTimezone>
                                <timezone>UTC</timezone>
                            </invoiceDate>
                            <invoicePrice>
                                <value>21.73</value>
                                <currencyIso>USD</currencyIso>
                            </invoicePrice>
                        </invoices>
                        <bsmItems>
                            <itemIdClientSystem>80000061_10</itemIdClientSystem>
                            <itemNumber>10</itemNumber>
                            <material>
                                <materialId>TG12</materialId>
                            </material>
                            <invoiceIdClientSystem>SAP_JNH_080_BILLING_DOC_90000037</invoiceIdClientSystem>
                            <grossMass>
                                <value>100.000</value>
                                <unit>kg</unit>
                            </grossMass>
                            <netMass>
                                <value>90.000</value>
                                <unit>kg</unit>
                            </netMass>
                            <netPrice>
                                <value>21.73</value>
                                <currencyIso>USD</currencyIso>
                            </netPrice>
                            <statisticalValue>
                                <value>21.73</value>
                                <currencyIso>USD</currencyIso>
                            </statisticalValue>
                            <clientSpecificFields>
                                <fields>
                                    <identCode>ORDER_TYPE</identCode>
                                    <value>TA</value>
                                </fields>
                                <fields>
                                    <identCode>ORDER_ITEM_TYPE</identCode>
                                    <value>TAN</value>
                                </fields>
                            </clientSpecificFields>
                            <classifications>
                                <classificationType>COCOEXPORT</classificationType>
                                <classificationValue>87100000</classificationValue>
                            </classifications>
                            <goodsDescription>
                                <languageISOCode>EN</languageISOCode>
                                <text>Trad.Good 12,Reorder Point,Reg.Trad.</text>
                            </goodsDescription>
                            <goodsDescription>
                                <languageISOCode>DE</languageISOCode>
                                <text>HAWA 12, Bestellpunkt, normaler Handel</text>
                            </goodsDescription>
                            <quantities>
                                <quantityType>ITEM</quantityType>
                                <quantity>
                                    <value>1.000</value>
                                    <unit>St</unit>
                                </quantity>
                            </quantities>
                            <licenseData>
                                <licenses>
                                    <customsProcessCountryCode>DE</customsProcessCountryCode>
                                    <licenseTypeCode>3LLB/81E</licenseTypeCode>
                                    <licenseNumber>666</licenseNumber>
                                    <licenseValidFromDate>
                                        <dateInTimezone>2025-09-10 12:00:00</dateInTimezone>
                                        <timezone>UTC</timezone>
                                    </licenseValidFromDate>
                                    <licenseExpirationDate>
                                        <dateInTimezone>2040-05-10 12:00:00</dateInTimezone>
                                        <timezone>UTC</timezone>
                                    </licenseExpirationDate>
                                    <decrementValue/>
                                    <decrementQuantity>
                                        <value>1.0000000</value>
                                        <unit>St</unit>
                                    </decrementQuantity>
                                </licenses>
                            </licenseData>
                            <interactionControls>
                                <usecase>
                                    <usecaseId>EC_APPROVAL_DATA</usecaseId>
                                </usecase>
                                <ids>
                                    <boIdClientSystem>SAP_JNH_080_OUTBOUND_DELIVERY_80000061$DEFAULT</boIdClientSystem>
                                    <clientSystemId>PGTEST1BSM_ATC_TEST</clientSystemId>
                                    <boItemIdClientSystem>10</boItemIdClientSystem>
                                </ids>
                            </interactionControls>
                        </bsmItems>
                    </bsmDeliveries>
                    <costs>
                        <costType>NET_PRICE</costType>
                        <value>
                            <value>21.73</value>
                            <currencyIso>USD</currencyIso>
                        </value>
                    </costs>
                </bsmConsignment>
            </requestDTO>
        </urn:createConsignment>
    </soapenv:Body>
</soapenv:Envelope>
```
```json
{
  "clientSystemId": "SAP_E01",
  "clientIdentCode": "API_TEST_CLIENT",
  "userName": "USER",
  "resultLanguageIsoCodes": [
    "EN"
  ],
  "bsmConsignment": {
    "interactionControls": [
      {
        "usecase": {
          "usecaseId": "CCO_SHP_CUSTOMS_UPD"
        },
        "ids": [
          {
            "boIdClientSystem": "SAP_E01_800_BILLING_DOC_90000001",
            "clientSystemId": "SAP_E01"
          }
        ]
      }
    ],
    "consignmentIdClientSystem": "SAP_E01_800_BILLING_DOC_90000001",
    "organizationUnitClientSystem": "DEFAULT",
    "consignmentNumber": "90000001",
    "profileCode": "INVOICE_STD",
    "personInCharge": {
      "forename": "Jan",
      "surname": "Ambrosch"
    },
    "bsmDeliveries": [
      {
        "deliveryIdClientSystem": "SAP_E01_800_BILLING_DOC_90000001",
        "organizationUnitClientSystem": "DEFAULT",
        "deliveryNumber": "90000001",
        "remark": "90000001",
        "dispatchCountryCode": "DE",
        "destinationCountryCode": "US",
        "decisiveDate": {
          "dateInTimezone": "2026-01-20 00:00:00",
          "timezone": "CET"
        },
        "tradeTerms": {
          "incotermCode": "EXW",
          "place": "Walldorf"
        },
        "clientSpecificFields": {},
        "parties": [
          {
            "partyType": "SHIPPING_POINT",
            "companyNumber": "1010",
            "street": "Dietmar-Hopp-Allee",
            "city": "Walldorf",
            "postCode": "69190",
            "country": "DE",
            "countryRegionCode": "BW"
          },
          {
            "partyType": "DECLARANT",
            "companyNumber": "1010",
            "name": "DE Company Code",
            "city": "Walldorf",
            "country": "DE"
          },
          {
            "partyType": "EXPORTER",
            "companyNumber": "1010",
            "name": "DE Company Code",
            "city": "Walldorf",
            "country": "DE"
          },
          {
            "partyType": "BUYER",
            "companyNumber": "10100050",
            "name": "Ausländischer Kunde 50 (US)",
            "street": "Confederate Ave 15400",
            "city": "Baton Rouge",
            "postCode": "70817-3609",
            "country": "US"
          },
          {
            "partyType": "CONSIGNOR",
            "companyNumber": "1010",
            "street": "Dietmar-Hopp-Allee",
            "city": "Walldorf",
            "postCode": "69190",
            "country": "DE",
            "countryRegionCode": "BW"
          },
          {
            "partyType": "CONSIGNEE",
            "companyNumber": "10100050",
            "name": "Ausländischer Kunde 50 (US)",
            "street": "Confederate Ave 15400",
            "city": "Baton Rouge",
            "postCode": "70817-3609",
            "country": "US"
          },
          {
            "partyType": "SELLER",
            "companyNumber": "1010",
            "city": "Walldorf",
            "country": "DE"
          }
        ],
        "invoices": [
          {
            "invoiceIdClientSystem": "SAP_JNH_080_BILLING_DOC_90000037",
            "invoiceNumber": "90000037",
            "invoiceDate": {
              "dateInTimezone": "2026-01-20 01:00:00",
              "timezone": "UTC"
            },
            "invoicePrice": {
              "value": 21.73,
              "currencyIso": "USD"
            }
          }
        ],
        "bsmItems": [
          {
            "itemIdClientSystem": "80000061_10",
            "itemNumber": "10",
            "material": {
              "materialId": "TG12"
            },
            "invoiceIdClientSystem": "SAP_JNH_080_BILLING_DOC_90000037",
            "grossMass": {
              "value": 100.0,
              "unit": "kg"
            },
            "netMass": {
              "value": 90.0,
              "unit": "kg"
            },
            "netPrice": {
              "value": 21.73,
              "currencyIso": "USD"
            },
            "statisticalValue": {
              "value": 21.73,
              "currencyIso": "USD"
            },
            "clientSpecificFields": {
              "fields": [
                {
                  "identCode": "ORDER_TYPE",
                  "value": "TA"
                },
                {
                  "identCode": "ORDER_ITEM_TYPE",
                  "value": "TAN"
                }
              ]
            },
            "classifications": [
              {
                "classificationType": "COCOEXPORT",
                "classificationValue": "87100000"
              }
            ],
            "goodsDescription": [
              {
                "languageISOCode": "EN",
                "text": "Trad.Good 12,Reorder Point,Reg.Trad."
              },
              {
                "languageISOCode": "DE",
                "text": "HAWA 12, Bestellpunkt, normaler Handel"
              }
            ],
            "quantities": [
              {
                "quantityType": "ITEM",
                "quantity": {
                  "value": 1.0,
                  "unit": "St"
                }
              }
            ],
            "licenseData": {
              "licenses": [
                {
                  "customsProcessCountryCode": "DE",
                  "licenseTypeCode": "3LLB/81E",
                  "licenseNumber": "666",
                  "licenseValidFromDate": {
                    "dateInTimezone": "2025-09-10 12:00:00",
                    "timezone": "UTC"
                  },
                  "licenseExpirationDate": {
                    "dateInTimezone": "2040-05-10 12:00:00",
                    "timezone": "UTC"
                  },
                  "decrementValue": null,
                  "decrementQuantity": {
                    "value": 1.0,
                    "unit": "St"
                  }
                }
              ]
            },
            "interactionControls": [
              {
                "usecase": {
                  "usecaseId": "EC_APPROVAL_DATA"
                },
                "ids": [
                  {
                    "boIdClientSystem": "SAP_JNH_080_OUTBOUND_DELIVERY_80000061$DEFAULT",
                    "clientSystemId": "PGTEST1BSM_ATC_TEST",
                    "boItemIdClientSystem": "10"
                  }
                ]
              }
            ]
          }
        ]
      }
    ],
    "costs": [
      {
        "costType": "NET_PRICE",
        "value": {
          "value": 21.73,
          "currencyIso": "USD"
        }
      }
    ]
  }
}
```

The difference to the createConsigment-API of Customs Managment is that is the part with the fields interactionControls.

Those fields are on consignment level and on item level. Here the example for the usecase Paperless Trade in context of Carrier Connect. This one is on consignment-Level.

```json
 "interactionControls": [
      {
        "usecase": {
          "usecaseId": "CCO_SHP_CUSTOMS_UPD"
        },
        "ids": [
          {
            "boIdClientSystem": "SAP_E01_800_BILLING_DOC_90000001",
            "clientSystemId": "SAP_E01"
          }
        ]
      }
```
```xml
<interactionControls>
  <usecase>
    <usecaseId>CCO_SHP_CUSTOMS_UPD</usecaseId>
  </usecase>
  <ids>
    <boIdClientSystem>SAP_E01_800_BILLING_DOC_90000001</boIdClientSystem>
    <clientSystemId>SAP_E01</clientSystemId>
  </ids>
</interactionControls>
```

And here the part for the usecase in context of Export Controls & Approvals. This one is on item level.

```json
"interactionControls": [
              {
                "usecase": {
                  "usecaseId": "EC_APPROVAL_DATA"
                },
                "ids": [
                  {
                    "boIdClientSystem": "SAP_JNH_080_OUTBOUND_DELIVERY_80000061$DEFAULT",
                    "clientSystemId": "PGTEST1BSM_ATC_TEST",
                    "boItemIdClientSystem": "10"
                  }
                ]
              }
```
```xml
<interactionControls>
  <usecase>
    <usecaseId>EC_APPROVAL_DATA</usecaseId>
  </usecase>
  <ids>
    <boIdClientSystem>SAP_JNH_080_OUTBOUND_DELIVERY_80000061$DEFAULT</boIdClientSystem>
    <clientSystemId>PGTEST1BSM_ATC_TEST</clientSystemId>
    <boItemIdClientSystem>10</boItemIdClientSystem>
  </ids>
</interactionControls>
```

Ok but that's not all. We have to synchronize the data from Customs Management to Carrier Connect & Export Controls.

For this the BSM has an extended Sync-API. 
