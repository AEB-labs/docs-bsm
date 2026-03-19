---
title: Transfer bill of materials
deprecated: false
hidden: false
metadata:
  robots: index
next:
  description: Go on with sales orders.
  pages:
    - slug: transfer-sales-orders
      title: Transfer sales orders
      type: basic
---
<br />

In the following you can see an API-Call of transfer bill of materials with one bill of material.

<Table>
  <thead>
    <tr>
      <th>
        Technique
      </th>

      <th>
        Documentation
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        REST
      </td>

      <td>
        [transferBillOfMaterials](https://rz3.aeb.de/test2bsm/swagger/#/O%26P/transferBillOfMaterials)
      </td>
    </tr>

    <tr>
      <td>
        SOAP
      </td>

      <td>
        [Origin&PreferencesBF (WSDL)](https://rz3.aeb.de/test2bsm/servlet/bf/OriginAndPreferencesBF?WSDL)
        [transferBillOfMaterials (Java Doc)](https://rz3.aeb.de/test2bsm/servlet/bf/doc/OriginAndPreferencesBF/de/aeb/xnsg/onpintegration/bf/onp/IOriginAndPreferencesBF.html#transferBillOfMaterials\(de.aeb.xnsg.onpintegration.bf.onp.TransferBillOfMaterialsRequestDTO\))
      </td>
    </tr>
  </tbody>
</Table>

```json
{
  "clientSystemId": "ERP_SYSTEM_X",
  "clientIdentCode": "API_TEST",
  "userName": "API_TEST",
  "resultLanguageIsoCodes": [
    "en"
  ],
  "billOfMaterialRequests": [
    {
      "idHost": "id_123",
      "labelHost": "ID 123",
      "organizationalUnit": "1000",
      "referenceNo": "123",
      "isDeleted": false,
      "materialNo": "123",
      "materialNoInternal": "123",
      "orderItemReference": null,
      "description": "bill of material description",
      "createDate": "2026-10-02",
      "modifyDate": "2026-10-02",
      "validToDate": "2029-10-02",
      "quantity": 1,
      "quantityUnit": "ST",
      "value": 100,
      "manufactoringCosts": 200,
      "currency": "EUR",
      "lotSize": 1,
      "isHandledMinimal": true,
      "isMaterialSet": false,
      "isActive": true,
      "alternativeNo": "ALT_1",
      "productOrigin": "DE",
      "items": [
        {
          "itemIdHost": "1",
          "itemLabelHost": "1",
          "itemReferenceNo": "1",
          "isDeleted": true,
          "materialNo": "M-11",
          "materialNoInternal": "M-11",
          "materialOrderItemReference": null,
          "type": "X",
          "description": "Material Desc",
          "quantity": 1,
          "quantityUnit": "ST",
          "value": 100,
          "lotSize": 1
        }
      ]
    }
  ]
}
```
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:de.aeb.xnsg.onpintegration.bf.onp">
    <soapenv:Header/>
    <soapenv:Body>
        <urn:transferBillOfMaterials>
            <request>
                <clientIdentCode>AEB_TEST_CLIENT</clientIdentCode>
                <clientSystemId>ERP_SYSTEM_1</clientSystemId>
                <resultLanguageIsoCodes>EN</resultLanguageIsoCodes>
                <userName>PAUL</userName>
                <billOfMaterialRequests>
                    <idHost>id_123</idHost>
                    <labelHost>Id 123</labelHost>
                    <organizationalUnit>DE_1000</organizationalUnit>
                    <referenceNo>123</referenceNo>
                    <isDeleted>false</isDeleted>
                    <materialNo>123</materialNo>
                    <materialNoInternal>00000123</materialNoInternal>
                    <orderItemReference></orderItemReference>
                    <description>car</description>
                    <createDate>2026-10-02</createDate>
                    <modifyDate>2026-10-02</modifyDate>
                    <validToDate>2029-10-02</validToDate>
                    <quantity>1</quantity>
                    <quantityUnit>ST</quantityUnit>
                    <value>100</value>
                    <manufactoringCosts>200</manufactoringCosts>
                    <currency>EUR</currency>
                    <lotSize>1</lotSize>
                    <isHandledMinimal>true</isHandledMinimal>
                    <isMaterialSet>false</isMaterialSet>
                    <isActive>true</isActive>
                    <alternativeNo>5000</alternativeNo>
                    <productOrigin>DE</productOrigin>
                    <items>
                        <itemIdHost>1</itemIdHost>
                        <itemLabelHost>1</itemLabelHost>
                        <itemReferenceNo>1</itemReferenceNo>
                        <isDeleted>false</isDeleted>
                        <materialNo>M-11</materialNo>
                        <materialNoInternal>M-11</materialNoInternal>
                        <materialOrderItemReference></materialOrderItemReference>
                        <type>X</type>
                        <description>Other one</description>
                        <quantity>1</quantity>
                        <quantityUnit>ST</quantityUnit>
                        <value>100</value>
                        <lotSize>1</lotSize>
                    </items>
                </billOfMaterialRequests>
            </request>
        </urn:transferBillOfMaterials>
    </soapenv:Body>
</soapenv:Envelope>
```

And here you can see the response of the request.

```json
{
  "hasErrors": false,
  "hasOnlyRetryableErrors": false,
  "hasWarnings": false,
  "messages": [],
  "responses": [
    {
      "hasErrors": false,
      "hasWarnings": false,
      "messages": [],
      "idHost": "id_123"
    }
  ]
}
```
```xml
<?xml version="1.0" encoding="UTF-8"?>
<S:Envelope xmlns:S="http://schemas.xmlsoap.org/soap/envelope/">
    <S:Body>
        <ns2:transferBillOfMaterialsResponse xmlns:ns2="urn:de.aeb.xnsg.onpintegration.bf.onp">
            <result>
                <hasErrors>false</hasErrors>
                <hasOnlyRetryableErrors>false</hasOnlyRetryableErrors>
                <hasWarnings>false</hasWarnings>
                <responses>
                    <hasErrors>false</hasErrors>
                    <hasWarnings>false</hasWarnings>
                    <idHost>id_123</idHost>
                </responses>
            </result>
        </ns2:transferBillOfMaterialsResponse>
    </S:Body>
</S:Envelope>
```

In case of an error it looks like this.

```json
{
  "hasErrors": true,
  "hasOnlyRetryableErrors": false,
  "hasWarnings": false,
  "messages": [
    {
      "messageType": "ERROR",
      "messageIdentCode": "EMPTY_MANDATORY_FIELD",
      "messageTexts": [
        {
          "languageISOCode": "en",
          "text": "The mandatory field \"idHost\" must be filled."
        }
      ],
      "indentationLevel": 0
    }
  ]
}
```
```xml
<?xml version="1.0" encoding="UTF-8"?>
<S:Envelope xmlns:S="http://schemas.xmlsoap.org/soap/envelope/">
    <S:Body>
        <ns2:transferBillOfMaterialsResponse xmlns:ns2="urn:de.aeb.xnsg.onpintegration.bf.onp">
            <result>
                <hasErrors>true</hasErrors>
                <hasOnlyRetryableErrors>false</hasOnlyRetryableErrors>
                <hasWarnings>false</hasWarnings>
                <messages>
                    <messageType>ERROR</messageType>
                    <messageIdentCode>EMPTY_MANDATORY_FIELD</messageIdentCode>
                    <messageTexts>
                        <languageISOCode>en</languageISOCode>
                        <text>The mandatory field "idHost" must be filled.</text>
                    </messageTexts>
                    <indentationLevel>0</indentationLevel>
                </messages>
            </result>
        </ns2:transferBillOfMaterialsResponse>
    </S:Body>
</S:Envelope>
```
