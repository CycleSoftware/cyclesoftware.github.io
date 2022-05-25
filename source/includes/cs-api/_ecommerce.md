# E-commerce #

The e-commerce APIs are designed for pushing e-commerce orders to CycleSoftware.

***Authentication***

The authentication is handled in the `Authentication` element of the SOAP requests.

| Field       | Type   | Description                                            |
|-------------|--------|--------------------------------------------------------|
| `username`  | string | API credentials username                               |
| `password`  | string | API credentials password                               |
| `dealer_id` | string | Leave empty or specify the store_id or use the API-key |

***Scope(s)***

- `e-commerce`

### Definition ###

The latest definition of the WSDL specification can be found at:

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">WSDL-SOAP</i>
		<h6>/app/cs/api/ecommerce/soap_2_9/?wsdl</h6>
	</div>
</div>

## Properties ##

| Property                                                                | Type      | Description                                                                                                                                                                                                                                                                                         |
|-------------------------------------------------------------------------|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Authentication[].username`                                             | `string`  | e.g. `your-username`                                                                                                                                                                                                                                                                                |
| `Authentication[].password`                                             | `string`  | e.g. `your-password`                                                                                                                                                                                                                                                                                |
| `Authentication[].dealer_id`                                            | `string`  | store-id or api-key. e.g. `1`                                                                                                                                                                                                                                                                       |
| `Order.order_reference_id`                                              | `string`  | Unique order reference id `319813049`                                                                                                                                                                                                                                                               |
| `Order.order_reference_text`                                            | `string`  | Unique order reference text `5640c085abba9`                                                                                                                                                                                                                                                         |
| `Order.order_is_payed`                                                  | `boolean` | boolean `1` or `0`                                                                                                                                                                                                                                                                                  |
| `Order.order_payment_method_description`                                | `string`  | Use “psp” for payments using a Payment service Provider (e.g. iDEAL, Bancontact etc.): `psp`,`pin`,`bancontact`,`contant`,`chip`,`creditcard`,`bank`,`rembours`,`ecocheques`                                                                                                                        |
| `Order.order_ship_to_customer`                                          | `boolean` | boolean `1` or `0`                                                                                                                                                                                                                                                                                  |
| `Order.order_shipment_method_description`                               | `string`  | e.g. `tnt`                                                                                                                                                                                                                                                                                          |
| `Order.order_date_preferred_delivery`                                   | `date`    | e.g. `2015-12-01`                                                                                                                                                                                                                                                                                   |
| `Order.order_remarks`                                                   | `string`  | e.g. `remark example`                                                                                                                                                                                                                                                                               |
| `Order.order_vat_country_code`                                          | `string`  | Apply the VAT rates of this country code. CS will only apply the VAT rates if enabled in account settings and if order_ship_to_customer is true. If the VAT rates are not applied or the same as the country of the account, it will default back to null in the OrderStatusResponse                |
| `Order.order_sales_employee_id`                                         | `integer` | e.g. `10001` see Common / Employees endpoint for employee_id values                                                                                                                                                                                                                                 |
| `Order.Customer`                                                        | `object`  | see Customer.* property                                                                                                                                                                                                                                                                             |
| `Order.Customer.DeliveryAddress.delivery_address_use_delivery_address`  | `boolean` | Boolean `1` or `0`                                                                                                                                                                                                                                                                                  |
| `Order.Customer.DeliveryAddress.delivery_address_name`                  | `string`  | e.g. `CycleSoftware`                                                                                                                                                                                                                                                                                |
| `Order.Customer.DeliveryAddress.delivery_address_street_name`           | `string`  | e.g. `Kievitsven`                                                                                                                                                                                                                                                                                   |
| `Order.Customer.DeliveryAddress.delivery_address_postal_code`           | `string`  | e.g. `5249JJ`                                                                                                                                                                                                                                                                                       |
| `Order.Customer.DeliveryAddress.delivery_address_housenumber`           | `string`  | e.g. `4`                                                                                                                                                                                                                                                                                            |
| `Order.Customer.DeliveryAddress.delivery_address_housenumber_suffix`    | `string`  | e.g. `b`                                                                                                                                                                                                                                                                                            |
| `Order.Customer.DeliveryAddress.delivery_address_city`                  | `string`  | e.g. `Rosmalen`                                                                                                                                                                                                                                                                                     |
| `Order.Customer.DeliveryAddress.delivery_address_country_code_iso_3166` | `string`  | e.g. `NL`                                                                                                                                                                                                                                                                                           |
| `Order.Customer.DeliveryAddress.delivery_address_remarks`               | `string`  | e.g. `Bam`                                                                                                                                                                                                                                                                                          |
| `Order.OrderItems.OrderItem`                                            | `array`   | Array of OrderItem objects                                                                                                                                                                                                                                                                          |
| `Order.OrderItems.OrderItem[].order_item_is_bicycle`                    | `boolean` | Indicate whether this order item is a sold bicycle (0 or 1)                                                                                                                                                                                                                                         |
| `Order.OrderItems.OrderItem[].order_item_barcode`                       | `string`  | e.g. `1000`                                                                                                                                                                                                                                                                                         |
| `Order.OrderItems.OrderItem[].order_item_quantity`                      | `integer` | e.g. `2`                                                                                                                                                                                                                                                                                            |
| `Order.OrderItems.OrderItem[].order_item_description`                   | `string`  | e.g. `Test product`                                                                                                                                                                                                                                                                                 |
| `Order.OrderItems.OrderItem[].order_item_unit_price_in_vat`             | `decimal` | e.g. `12.99`                                                                                                                                                                                                                                                                                        |
| `Order.OrderItems.OrderItem[].order_item_unit_discount_amount_in_vat`   | `decimal` | e.g. `2.99`                                                                                                                                                                                                                                                                                         |
| `Order.OrderItems.OrderItem[].order_item_vat_code`                      | `integer` | `0`: no VAT, `1`: Low VAT, `2` High VAT                                                                                                                                                                                                                                                             |
| `Order.OrderItems.OrderItem[].order_item_supplier_order_mode`           | `string`  | 0: no supplier order or reservation on objects<br/>1:automatically create supplier order for this sales order<br/>2: automatically reserve available stock objects based on the object_id in order_item_object_id or order_item_barcode field.<br/>4: Same as mode=2 with pool orders via warehouse |
| `Order.OrderItems.OrderItem[].order_item_supplier_id`                   | `integer` | When order_item_supplier_mode = 1, make the supplier order for this supplier. Supplier IDs can be looked up in   https://api.cyclesoftware.nl/app/api/groups/                                                                                                                                       |
| `Order.OrderItems.OrderItem[].order_item_object_id`                     | `integer` | Reserve this specific object for this order item                                                                                                                                                                                                                                                    |
| `Order.OrderItems.OrderItem[].order_item_invoice_customer_id`           | `integer` | If supplied with integer value > 0 this order item will be invoiced to this customer id (SplitOrder) All the customer info in the SaveOrder should be the “rider” or “consumer”                                                                                                                     |
| `UpdateValues.UpdateValue`                                              | `array`   | Array of UpdateValue objects                                                                                                                                                                                                                                                                        |
| `UpdateValues.UpdateValue[].name`                                       | `string`  | Field to update: `order_reference_text`, `order_is_payed`,`order_payment_method_description`,`order_ship_to_customer`,`order_shipment_method_description`,`order_date_preferred_delivery`,`order_track_trace_reference`,`order_remarks`                                                             |
| `UpdateValues.UpdateValue[].value`                                      | `string`  | e.g. `Will pickup at 13.00`                                                                                                                                                                                                                                                                         |
| `Customer.customer_type_name`                                           | `string`  | One of the following: `Klant`, `Leverancier`, `E-commerce`, `Zakelijk`, `Lease-rijder`, `Lease-maatschappij`, `Werkgever`                                                                                                                                                                           |
| `Customer.customer_cs_customer_id`                                      | `string`  | e.g. `235238848`                                                                                                                                                                                                                                                                                    |
| `Customer.customer_reference`                                           | `string`  | Should be an unique reference to the customer to prevent re-use / overwrites of existing customers                                                                                                                                                                                                  |
| `Customer.customer_name_prefix`                                         | `string`  | e.g. `Dhr.`                                                                                                                                                                                                                                                                                         |
| `Customer.customer_name_initials`                                       | `string`  | e.g. `A`                                                                                                                                                                                                                                                                                            |
| `Customer.customer_middle_name`                                         | `string`  | e.g. `Van`                                                                                                                                                                                                                                                                                          |
| `Customer.customer_last_name`                                           | `string`  | e.g. `Name 235238848`                                                                                                                                                                                                                                                                               |
| `Customer.customer_postal_code`                                         | `string`  | e.g. `8448PE`                                                                                                                                                                                                                                                                                       |
| `Customer.customer_housenumber`                                         | `string`  | e.g. `32`                                                                                                                                                                                                                                                                                           |
| `Customer.customer_housenumber_suffix`                                  | `string`  | e.g. `B`                                                                                                                                                                                                                                                                                            |
| `Customer.customer_street_name`                                         | `string`  | e.g. `Mauritslaan`                                                                                                                                                                                                                                                                                  |
| `Customer.customer_city`                                                | `string`  | e.g. `Heerenveen`                                                                                                                                                                                                                                                                                   |
| `Customer.customer_phone`                                               | `string`  | e.g. `073-1234567`                                                                                                                                                                                                                                                                                  |
| `Customer.customer_mobile`                                              | `string`  | e.g. `06-124235335`                                                                                                                                                                                                                                                                                 |
| `Customer.customer_country_code_iso_3166`                               | `string`  | Country code iso3166 e.g. `NL`                                                                                                                                                                                                                                                                      |
| `Customer.customer_email`                                               | `string`  | e.g. `test235238848@cyclesoftware.nl`                                                                                                                                                                                                                                                               |
| `Customer.customer_newsletter`                                          | `boolean` | Toggle newsletter option boolean `1` or `0`                                                                                                                                                                                                                                                         |
| `Customer.customer_date_of_birth`                                       | `date`    | e.g. `1980-01-01`                                                                                                                                                                                                                                                                                   |
| `Customer.customer_iban`                                                | `string`  | e.g. `NL69INGB0123456789`                                                                                                                                                                                                                                                                           |

## SaveOrder ##

Creates a new order in CycleSoftware

```php
<?php


try {
    $client = new \SoapClient(
        'https://api.cyclesoftware.nl/app/cs/api/ecommerce/soap_2_9/?wsdl',
        [
            'trace' => true,
            'use' => SOAP_LITERAL,
            'encoding' => 'UTF-8',
        ]
    );
   $input = (object)[
        'Authentication' =>
            (object)[
                'username' => 'your-username',
                'password' => 'your-password',
                'dealer_id' => '1', // store-id within account
            ],
        'Order' =>
            (object)[
                'order_reference_text' => '5640c085abba9',
                'order_reference_id' => '319813049',
                'order_is_payed' => '1',
                'order_payment_method_description' => 'psp',
                'order_ship_to_customer' => '1',
                'order_shipment_method_description' => 'tnt',
                'order_date_preferred_delivery' => '2015-12-01',
                'order_remarks' => 'remark example',
                'order_vat_country_code' => 'NL',
                'order_sales_employee_id ' => null,
                'Customer' =>
                    (object)[
                        'customer_cs_customer_id' => '11',
                        'customer_reference' => 'unique-reference-customer',
                        'customer_name_prefix' => 'Dhr.',
                        'customer_name_initials' => 'J',
                        'customer_middle_name' => 'van',
                        'customer_last_name' => 'Dijk',
                        'customer_postal_code' => '1000AA',
                        'customer_housenumber' => '2',
                        'customer_housenumber_suffix' => 'B',
                        'customer_street_name' => 'Steenweg',
                        'customer_city' => 'Amsterdam',
                        'customer_phone' => '0733030050',
                        'customer_mobile' => '0612345678',
                        'customer_country_code_iso_3166' => 'NL',
                        'customer_email' => 'test@test.com',
                        'customer_newsletter' => '1',
                        'customer_date_of_birth' => '',
                        'customer_iban' => '',
                        'DeliveryAddress' =>
                            (object)[
                                'delivery_address_use_delivery_address' => '1',
                                'delivery_address_name' => 'Bedrijfsnaam',
                                'delivery_address_street_name' => 'Steenweg',
                                'delivery_address_postal_code' => '1000AA',
                                'delivery_address_housenumber' => '2',
                                'delivery_address_housenumber_suffix' => 'B',
                                'delivery_address_city' => 'Amsterdam',
                                'delivery_address_country_code_iso_3166' => 'NL',
                                'delivery_address_remarks' => 'Extra opmerking',
                            ],
                    ],
                'OrderItems' =>
                    (object)[
                        'OrderItem' =>
                            [
                                    (object)[
                                        'order_item_is_bicycle' => '0',
                                        'order_item_barcode' => '88237237239',
                                        'order_item_quantity' => '-1',
                                        'order_item_description' => 'Some article',
                                        'order_item_unit_price_in_vat' => '1021',
                                        'order_item_unit_discount_amount_in_vat' => '21',
                                        'order_item_vat_code' => '2',
                                        'order_item_supplier_order_mode' => '0',
                                        'order_item_invoice_customer_id' => 4,
                                    ],
                                    (object)[
                                        'order_item_is_bicycle' => '0',
                                        'order_item_barcode' => '47348340934',
                                        'order_item_quantity' => '1',
                                        'order_item_description' => 'Some Article',
                                        'order_item_unit_price_in_vat' => '1521',
                                        'order_item_unit_discount_amount_in_vat' => '21',
                                        'order_item_vat_code' => '2',
                                        'order_item_supplier_order_mode' => '0',
                                        'order_item_invoice_customer_id' => '2',
                                    ],
                                    (object)[
                                        'order_item_is_bicycle' => '0',
                                        'order_item_barcode' => '43934939344',
                                        'order_item_quantity' => '3',
                                        'order_item_description' => 'Some article',
                                        'order_item_unit_price_in_vat' => '1021',
                                        'order_item_unit_discount_amount_in_vat' => '21',
                                        'order_item_vat_code' => '2',
                                        'order_item_supplier_order_mode' => '0',
                                        'order_item_invoice_customer_id' => null,
                                    ],
                            ],
                    ],
            ],
    ];
    $result = $client->SaveOrder($input);
    $order_id = $result->order_id;
    $customer_id = $result->customer_id;
    var_dump($result);
}
catch (\SoapFault $e) {
    var_dump($e->getMessage());
}
```

> HTTP Request

```http
POST /app/cs/api/ecommerce/soap_2_9/ HTTP/1.1
Host: api.cyclesoftware.nl
Accept-encoding: gzip,deflate
Accept: text/xml
Content-type: text/xml; charset=utf-8
User-agent: SoapClient
Soapaction: "SaveOrder"
Content-length: 4614

<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://api.cyclesoftware.nl/app/cs/api/ecommerce/soap_2_1/">
  <SOAP-ENV:Body>
    <ns1:SaveOrderRequest>
      <Authentication>
        <username>your-username</username>
        <password>your-password</password>
        <dealer_id>1</dealer_id>
      </Authentication>
      <Order>
        <order_reference_id>319813049</order_reference_id>
        <order_reference_text>5640c085abba9</order_reference_text>
        <order_is_payed>1</order_is_payed>
        <order_payment_method_description>psp</order_payment_method_description>
        <order_ship_to_customer>1</order_ship_to_customer>
        <order_shipment_method_description>tnt</order_shipment_method_description>
        <order_date_preferred_delivery>2015-12-01</order_date_preferred_delivery>
        <order_remarks>remark example</order_remarks>
        <order_vat_country_code>NL</order_vat_country_code>
        <order_sales_employee_id/>
        <Customer>
          <customer_cs_customer_id>0</customer_cs_customer_id>
          <customer_reference>unique-reference-customer</customer_reference>
          <customer_name_prefix>J</customer_name_prefix>
          <customer_middle_name>van</customer_middle_name>
          <customer_last_name>Dijk</customer_last_name>
          <customer_postal_code>1000AA</customer_postal_code>
          <customer_housenumber>2</customer_housenumber>
          <customer_housenumber_suffix>B</customer_housenumber_suffix>
          <customer_street_name>Steenweg</customer_street_name>
          <customer_city>Amsterdam</customer_city>
          <customer_phone>0733030050</customer_phone>
          <customer_mobile>0612345678</customer_mobile>
          <customer_country_code_iso_3166>NL</customer_country_code_iso_3166>
          <customer_email>test@test.com</customer_email>
          <customer_newsletter>1</customer_newsletter>
          <customer_iban>NL69INGB0123456789</customer_iban>
          <customer_date_of_birth>1988-09-29</customer_date_of_birth>
          <DeliveryAddress>
            <delivery_address_use_delivery_address>1</delivery_address_use_delivery_address>
            <delivery_address_name>CycleSoftware</delivery_address_name>
            <delivery_address_street_name>Kievitsven</delivery_address_street_name>
            <delivery_address_postal_code>5249JJ</delivery_address_postal_code>
            <delivery_address_housenumber>4</delivery_address_housenumber>
            <delivery_address_housenumber_suffix>b</delivery_address_housenumber_suffix>
            <delivery_address_city>Rosmalen</delivery_address_city>
            <delivery_address_country_code_iso_3166>NL</delivery_address_country_code_iso_3166>
            <delivery_address_remarks>Bam</delivery_address_remarks>
          </DeliveryAddress>
        </Customer>
        <OrderItems>
          <OrderItem>
            <order_item_is_bicycle>0</order_item_is_bicycle>
            <order_item_barcode>1000</order_item_barcode>
            <order_item_quantity>2</order_item_quantity>
            <order_item_description>DescriptionTest</order_item_description>
            <order_item_unit_price_in_vat>12.99</order_item_unit_price_in_vat>
            <order_item_unit_discount_amount_in_vat>2.99</order_item_unit_discount_amount_in_vat>
            <order_item_vat_code>2</order_item_vat_code>
            <order_item_supplier_order_mode>0</order_item_supplier_order_mode>
            <order_item_supplier_id>0</order_item_supplier_id>
            <order_item_object_id>0</order_item_object_id>
            <order_item_invoice_customer_id>0</order_item_invoice_customer_id>
          </OrderItem>
          <OrderItem>
            <order_item_is_bicycle>0</order_item_is_bicycle>
            <order_item_barcode>1000</order_item_barcode>
            <order_item_quantity>2</order_item_quantity>
            <order_item_description>DescriptionTest</order_item_description>
            <order_item_unit_price_in_vat>12.99</order_item_unit_price_in_vat>
            <order_item_unit_discount_amount_in_vat>2.99</order_item_unit_discount_amount_in_vat>
            <order_item_vat_code>2</order_item_vat_code>
            <order_item_supplier_order_mode>0</order_item_supplier_order_mode>
            <order_item_supplier_id>0</order_item_supplier_id>
            <order_item_object_id>0</order_item_object_id>
            <order_item_invoice_customer_id>1000</order_item_invoice_customer_id>
          </OrderItem>
        </OrderItems>
      </Order>
    </ns1:SaveOrderRequest>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>


HTTP/1.1 200 
Content-type: application/xml; charset=utf-8
Content-length: 2083

<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
  <SOAP-ENV:Body>
    <SaveOrderResponse>
      <order_id>3688</order_id>
      <customer_id>1498</customer_id>
      <created_new_order>1</created_new_order>
      <remarks>
      </remarks>
      <OrderItems>
        <OrderItem>
          <order_item_status_id>0</order_item_status_id>
          <order_item_status_text>Geen status</order_item_status_text>
          <order_item_is_bicycle>0</order_item_is_bicycle>
          <order_item_object_id>0</order_item_object_id>
          <order_item_barcode>1000</order_item_barcode>
          <order_item_quantity>2</order_item_quantity>
          <order_item_description>Test product</order_item_description>
          <order_item_unit_price_in_vat>12.99</order_item_unit_price_in_vat>
          <order_item_unit_discount_amount_in_vat>2.99</order_item_unit_discount_amount_in_vat>
          <order_item_vat_code>2</order_item_vat_code>
          <order_item_line_id>1</order_item_line_id>
          <order_item_object_id/>
          <order_item_invoice_customer_id/>
        </OrderItem>
        <OrderItem>
          <order_item_status_id>0</order_item_status_id>
          <order_item_status_text>Geen status</order_item_status_text>
          <order_item_is_bicycle>0</order_item_is_bicycle>
          <order_item_object_id>0</order_item_object_id>
          <order_item_barcode>1000</order_item_barcode>
          <order_item_quantity>2</order_item_quantity>
          <order_item_description>Test product</order_item_description>
          <order_item_unit_price_in_vat>12.99</order_item_unit_price_in_vat>
          <order_item_unit_discount_amount_in_vat>2.99</order_item_unit_discount_amount_in_vat>
          <order_item_vat_code>2</order_item_vat_code>
          <order_item_line_id>2</order_item_line_id>
          <order_item_object_id/>
          <order_item_invoice_customer_id>1000</order_item_invoice_customer_id>
        </OrderItem>
    </SaveOrderResponse>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

## UpdateOrder ##

Update some header fields in the sales order. The following fields can be updated:

```php
<?php

try {
    $client = new \SoapClient(
        'https://api.cyclesoftware.nl/app/cs/api/ecommerce/soap_2_9/?wsdl',
        [
            'trace' => true,
            'use' => SOAP_LITERAL,
            'encoding' => 'UTF-8',
        ]
    );
    $input = (object)[
        'Authentication' =>
            (object)[
                'username' => 'your-username',
                'password' => 'your-password',
                'dealer_id' => '1', // store-id within account
            ],
        'order_id' => '3623',
        'order_reference_id' => '',
        'UpdateValues' =>
            (object)[
                'UpdateValue' =>
                    [
                        0 =>
                            (object)[
                                'name' => 'order_date_preferred_delivery',
                                'value' => '2021-10-05 08:03:31',
                            ],
                        1 =>
                            (object)[
                                'name' => 'order_reference_text',
                                'value' => '615beab217c75',
                            ],
                        2 =>
                            (object)[
                                'name' => 'order_track_trace_reference',
                                'value' => '615beab217c76',
                            ],
                    ],
            ],
    ];
    $result = $client->UpdateOrder($input);
    var_dump($result);
}
catch (\SoapFault $e) {
    var_dump($e->getMessage());
}
```

> Request

```http
POST /app/cs/api/ecommerce/soap_2_9/ HTTP/1.1
Host: api.cyclesoftware.nl
Accept-encoding: gzip,deflate
Accept: text/xml
Content-type: text/xml; charset=utf-8
User-agent: SoapClient
Soapaction: "UpdateOrder"
Content-length: 846

<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://api.cyclesoftware.nl/app/cs/api/ecommerce/soap_2_1/">
  <SOAP-ENV:Body>
    <ns1:UpdateOrderRequest>
      <Authentication>
        <username>your-username</username>
        <password>your-password</password>
        <dealer_id>1</dealer_id>
      </Authentication>
      <order_id>3623</order_id>
      <order_reference_id>
      </order_reference_id>
      <UpdateValues>
        <UpdateValue>
          <name>order_date_preferred_delivery</name>
          <value>2015-11-09 15:50:35</value>
        </UpdateValue>
        <UpdateValue>
          <name>order_remarks</name>
          <value>Will pickup at 13.00</value>
        </UpdateValue>
      </UpdateValues>
    </ns1:UpdateOrderRequest>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>


HTTP/1.1 200 
Content-type: application/xml; charset=utf-8
Content-length: 2446

<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://api.cyclesoftware.nl/app/cs/api/ecommerce/soap_2_1/">
  <SOAP-ENV:Body>
    <ns1:OrderStatusResponse>
      <order_id>3623</order_id>
      <order_reference_text>563c8b1bc4ada</order_reference_text>
      <order_reference_id>-663982782</order_reference_id>
      <order_status_text>In behandeling</order_status_text>
      <order_track_trace_reference>563c8b1bc4ada</order_track_trace_reference>
      <order_date_preferred_delivery>2015-11-09 15:50:35</order_date_preferred_delivery>
      <order_vat_country_code/>
      <order_sales_employee_id>11111</order_sales_employee_id>
      <customer_id>1498</customer_id>
      <invoice_id>0</invoice_id>
      <OrderResultItems>
        <OrderResultItem>
          <order_item_status_id>0</order_item_status_id>
          <order_item_status_text>Geen status</order_item_status_text>
          <order_item_is_bicycle>1</order_item_is_bicycle>
          <order_item_barcode>1000</order_item_barcode>
          <order_item_quantity>2</order_item_quantity>
          <order_item_description>Test product</order_item_description>
          <order_item_unit_price_in_vat>10.00</order_item_unit_price_in_vat>
          <order_item_unit_discount_amount_in_vat>2.99</order_item_unit_discount_amount_in_vat>
          <order_item_vat_code>2</order_item_vat_code>
          <order_item_line_id>3</order_item_line_id>
          <order_item_object_id/>
          <order_item_invoice_customer_id/>
        </OrderResultItem>
        <OrderResultItem>
          <order_item_status_id>0</order_item_status_id>
          <order_item_status_text>Geen status</order_item_status_text>
          <order_item_is_bicycle>0</order_item_is_bicycle>
          <order_item_barcode>1000</order_item_barcode>
          <order_item_quantity>2</order_item_quantity>
          <order_item_description>Test product</order_item_description>
          <order_item_unit_price_in_vat>10.00</order_item_unit_price_in_vat>
          <order_item_unit_discount_amount_in_vat>2.99</order_item_unit_discount_amount_in_vat>
          <order_item_vat_code>2</order_item_vat_code>
          <order_item_line_id>5</order_item_line_id>
          <order_item_object_id>0</order_item_object_id>
          <order_item_invoice_customer_id>1000</order_item_invoice_customer_id>
        </OrderResultItem>
      </OrderResultItems>
    </ns1:OrderStatusResponse>
  </SOAP-ENV:Body>
```

## Create invoice(s) ##

Create invoice(s) for sales order. If the sales-order is split amongst several customers, the result will yield multiple
invoices.

- Scope(s): `e-commerce`

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">POST</i>
		<h6>/api/v1/sales/orders/:sales_order_id/create-invoices.json</h6>
	</div>
</div>

| URL parameter     | Type      | Description                                             |
|-------------------|-----------|---------------------------------------------------------|
| `:sales_order_id` | `integer` | Sales order ID <i class="label label-info">required</i> |

The following optional POST parameters can be used to specify specific behavior.

| POST parameter          | Type      | Default                                           | Description                                                                                              |
|-------------------------|-----------|---------------------------------------------------|----------------------------------------------------------------------------------------------------------|
| `employee_id`           | `integer` | The sales employee registered for the sales-order | Employee ID for registration                                                                             |
| `order_status_id`       | `integer` | `null`                                            | New sales order status. See common endpoint                                                              |
| `book`                  | `boolean` | `false`                                           | if `true`, the invoice will be booked in administration. Otherwise the invoice will be pro-forma         |
| `customer_messages`     | `boolean` | `true`                                            | if `true` a phone- of e-mail message will be sent (according to account settings) to inform the customer |
| `allow_resend_messages` | `integer` | `false`                                           | if `true` a phone- of e-mail message will be sent again if there were previous messages                  |

### Properties ###

| Property                                    | Type      | Nullable | Description                                      |
|---------------------------------------------|-----------|----------|--------------------------------------------------|
| `error`                                     | `boolean` | `false`  | `true` if an error occurred                      |
| `error_message`                             | `null`    | `true`   | Error message if occurred                        |
| `invoices`                                  | `array`   | `false`  | array of created invoices                        |
| `invoices[].invoice_number`                 | `integer` | `false`  | Invoice number e.g. `20173383`                   |
| `invoices[].customer_id`                    | `integer` | `false`  | Customer number of invoice e.g. `9011`           |
| `invoices[].sent_messages.phone_message`    | `boolean` | `false`  | `true` if a phone message was sent               |
| `invoices[].sent_messages.email_message`    | `boolean` | `false`  | `true` if an e-mail message was sent             |
| `invoices[].documents`                      | `array`   | `false`  | Array of generated documents                     |
| `invoices[].documents[].document_mime_type` | `string`  | `false`  | Mime type of the document e.g. `application/pdf` |
| `invoices[].documents[].document_base64`    | `string`  | `false`  | Base64 encoded string of document                |

> HTTP request

```http
POST /api/v1/sales/orders/1000/create-invoices.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip,deflate
Accept: application/json
Content-type: application/x-www-form-urlencoded; charset=utf-8
Content-length: 299

employee_id=1005&order_status_id=9&book=1&customer_messages=1&allow_resend_messages=1
```

> HTTP Response

```http
HTTP/1.1 200 
Content-type: application/json; charset=utf-8
Content-length: 900

{
    "error": false,
    "error_message": null,
    "invoices": [
        {
            "invoice_number": 20173382,
            "customer_id": 6298,
            "sent_messages": {
                "phone_message": true,
                "email_message": false
            },
            "documents": [
                {
                    "document_mime_type": "application/pdf",
                    "document_base64": "VBERi0xLjcKJ..."
                }
            ]
        },
        {
            "invoice_number": 20173383,
            "customer_id": 9011,
            "sent_messages": {
                "phone_message": false,
                "email_message": false
            },
            "documents": [
                {
                    "document_mime_type": "application/pdf",
                    "document_base64": "VBERi0xLjcKJ..."
                }
            ]
        }
    ]
}
```

## AddOrderItems ##

Add new order items to an existing order.

```php
try {
    $client = new \SoapClient(
        'https://api.cyclesoftware.nl/app/cs/api/ecommerce/soap_2_9/?wsdl',
        [
            'trace' => true,
            'use' => SOAP_LITERAL,
            'encoding' => 'UTF-8',
        ]
    );
    $input = (object)[
        'Authentication' =>
            (object)[
                'username' => 'your-username',
                'password' => 'your-password',
                'dealer_id' => '1', // store-id within account
            ],
        'order_id' => '684476',
        'order_reference_id' => '',
        'OrderItems' => (object)[
                'OrderItem' =>
                    [
                        (object)[
                            'order_item_is_bicycle' => '0',
                            'order_item_barcode' => '872382382323',
                            'order_item_quantity' => '2',
                            'order_item_description' => 'DescriptionTest',
                            'order_item_unit_price_in_vat' => '12.99',
                            'order_item_unit_discount_amount_in_vat' => '2.99',
                            'order_item_invoice_customer_id' => null,
                        ],
                        (object)[
                            'order_item_is_bicycle' => '0',
                            'order_item_barcode' => '4624824934349',
                            'order_item_quantity' => '2',
                            'order_item_description' => 'For lease company',
                            'order_item_unit_price_in_vat' => '12.99',
                            'order_item_unit_discount_amount_in_vat' => '2.99',
                            'order_item_vat_code' => '2',
                            'order_item_invoice_customer_id' => '10003',
                        ],
                    ],
            ],
    ];
    $result = $client->AddOrderItems($input);
    var_dump($result);
}
catch (\SoapFault $e) {
    var_dump($e->getMessage());
}
```

> Request

```http
POST /app/cs/api/ecommerce/soap_2_9/ HTTP/1.1
Host: api.cyclesoftware.nl
Accept-encoding: gzip,deflate
Accept: text/xml
Content-type: text/xml; charset=utf-8
User-agent: SoapClient
Soapaction: "AddOrderItems"
Content-length: 1373

<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://api.cyclesoftware.nl/app/cs/api/ecommerce/soap_2_1/">
  <SOAP-ENV:Body>
    <ns1:AddOrderItemsRequest>
      <Authentication>
        <username>your-username</username>
        <password>your-password</password>
        <dealer_id>1</dealer_id>
      </Authentication>
      <order_id>3692</order_id>
      <order_reference_id>
      </order_reference_id>
      <OrderItems>
        <OrderItem>
          <order_item_is_bicycle>0</order_item_is_bicycle>
          <order_item_barcode>5640c122a30b9</order_item_barcode>
          <order_item_quantity>2</order_item_quantity>
          <order_item_description>DescriptionTest</order_item_description>
          <order_item_unit_price_in_vat>12.99</order_item_unit_price_in_vat>
          <order_item_unit_discount_amount_in_vat>2.99</order_item_unit_discount_amount_in_vat>
          <order_item_vat_code>2</order_item_vat_code>
          <order_item_supplier_order_mode>0</order_item_supplier_order_mode>
          <order_item_supplier_id>0</order_item_supplier_id>
          <order_item_object_id>0</order_item_object_id>
          <order_item_invoice_customer_id>1000</order_item_invoice_customer_id>
        </OrderItem>
      </OrderItems>
    </ns1:AddOrderItemsRequest>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>


HTTP/1.1 200 
Content-type: application/xml; charset=utf-8
Content-length: 2464

<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://api.cyclesoftware.nl/app/cs/api/ecommerce/soap_2_1/">
  <SOAP-ENV:Body>
    <ns1:OrderStatusResponse>
      <order_id>3692</order_id>
      <order_reference_text>5640c122154db</order_reference_text>
      <order_reference_id>-319656665</order_reference_id>
      <order_status_text>In behandeling</order_status_text>
      <order_track_trace_reference>
      </order_track_trace_reference>
      <order_date_preferred_delivery>2015-12-01 00:00:00</order_date_preferred_delivery>
      <order_sales_employee_id>1212</order_sales_employee_id>
      <customer_id>1498</customer_id>
      <invoice_id>0</invoice_id>
      <OrderResultItems>
        <OrderResultItem>
          <order_item_status_id>0</order_item_status_id>
          <order_item_status_text>Geen status</order_item_status_text>
          <order_item_is_bicycle>1</order_item_is_bicycle>
          <order_item_barcode>1000</order_item_barcode>
          <order_item_quantity>2</order_item_quantity>
          <order_item_description>Test product</order_item_description>
          <order_item_unit_price_in_vat>10.00</order_item_unit_price_in_vat>
          <order_item_unit_discount_amount_in_vat>2.99</order_item_unit_discount_amount_in_vat>
          <order_item_vat_code>1</order_item_vat_code>
          <order_item_line_id>3</order_item_line_id>
          <order_item_object_id>0</order_item_object_id>
          <order_item_invoice_customer_id/>
        </OrderResultItem>
        <OrderResultItem>
          <order_item_status_id>0</order_item_status_id>
          <order_item_status_text>Geen status</order_item_status_text>
          <order_item_is_bicycle>0</order_item_is_bicycle>
          <order_item_barcode>5640c122a30b9</order_item_barcode>
          <order_item_quantity>2</order_item_quantity>
          <order_item_description>DescriptionTest</order_item_description>
          <order_item_unit_price_in_vat>10.00</order_item_unit_price_in_vat>
          <order_item_unit_discount_amount_in_vat>2.99</order_item_unit_discount_amount_in_vat>
          <order_item_vat_code>2</order_item_vat_code>
          <order_item_line_id>5</order_item_line_id>
          <order_item_object_id>0</order_item_object_id>
          <order_item_invoice_customer_id>1000</order_item_invoice_customer_id>
        </OrderResultItem>
      </OrderResultItems>
    </ns1:OrderStatusResponse>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

## GetInvoiceDocument ##

Get an invoice document based on the invoice-number.

```php
<?php
try {
    $client = new \SoapClient(
        'https://api.cyclesoftware.nl/app/cs/api/ecommerce/soap_2_9/?wsdl',
        [
          'trace' => true,
          'use' => SOAP_LITERAL,
          'encoding' => 'UTF-8',
        ]
    );
    $input = (object)[];
    $input->Authentication = (object)[];
    $input->Authentication->username = 'your-username';
    $input->Authentication->password = 'your-password';
    $input->Authentication->dealer_id = '1';
    $input->invoice_number = '44848';
    $result = $client->GetInvoiceDocument($input);
    var_dump($result);
} catch (\SoapFault $e) {
    var_dump($e->getMessage());
}
```

> Request

```http
POST /app/cs/api/ecommerce/soap_2_9/ HTTP/1.1
Host: api.cyclesoftware.nl
Accept-encoding: gzip,deflate
Accept: text/xml
Content-type: text/xml; charset=utf-8
User-agent: SoapClient
Soapaction: "GetInvoiceDocument"
Content-length: 514

<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://api.cyclesoftware.nl/app/cs/api/ecommerce/soap_2_0/">
  <SOAP-ENV:Body>
    <ns1:GetInvoiceDocumentRequest>
      <Authentication>
        <username>your-username</username>
        <password>your-password</password>
        <dealer_id>1</dealer_id>
      </Authentication>
      <invoice_number>44848</invoice_number>
    </ns1:GetInvoiceDocumentRequest>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>

HTTP/1.1 200
Content-type: application/xml; charset=utf-8
Content-length: 396

<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
  <SOAP-ENV:Body>
    <GetInvoiceDocumentResponse>
      <invoice_number>44848</invoice_number>
      <data>data:application/pdf;base64,JVBERi0xLjcKMyAwIG9iago8PC9UeXBlIC9QYWdlIC9QYXJlbnQgMS.....==</data>
    </GetInvoiceDocumentResponse>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

## GetOrderStatus ##

Get an invoice document based on the sales order id or order reference.

```php
<?php
try {
    $client = new \SoapClient(
        'https://api.cyclesoftware.nl/app/cs/api/ecommerce/soap_2_9/?wsdl',
        [
          'trace' => true,
          'use' => SOAP_LITERAL,
          'encoding' => 'UTF-8',
        ]
    );
    $input = (object)[];
    $input->Authentication = (object)[];
    $input->Authentication->username = 'your-username';
    $input->Authentication->password = 'your-password';
    $input->Authentication->dealer_id = '1';
    $input->order_id = '44848';
    $input->order_reference_id = '61a0d79989fa3';//optional
    $result = $client->GetOrderStatus($input);
    var_dump($result);
} catch (\SoapFault $e) {
    var_dump($e->getMessage());
}
```

> Request

```http
POST /app/cs/api/ecommerce/soap_2_9/ HTTP/1.1
Host: api.cyclesoftware.nl
Accept-encoding: gzip,deflate
Accept: text/xml
Content-type: text/xml; charset=utf-8
User-agent: SoapClient
Soapaction: "GetOrderStatus"
Content-length: 580

<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://api.cyclesoftware.nl/app/cs/api/ecommerce/soap_2_0/">
  <SOAP-ENV:Body>
    <ns1:GetInvoiceDocumentRequest>
      <Authentication>
        <username>your-username</username>
        <password>your-password</password>
        <dealer_id>1</dealer_id>
      </Authentication>
      <order_id>711075</order_id>
      <order_reference_id>61a0d79989fa3</order_reference_id>
    </ns1:GetInvoiceDocumentRequest>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>

HTTP/1.1 200
Content-type: application/xml; charset=utf-8
Content-length: 2595

<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:ns1="http://api.cyclesoftware.nl/app/cs/api/ecommerce/soap_2_0/">
  <SOAP-ENV:Body>
    <ns1:OrderStatusResponse>
      <order_id>711075</order_id>
      <order_reference_text>61a0d79989fa3</order_reference_text>
      <order_reference_id>1637930905565</order_reference_id>
      <order_status_text>In behandeling</order_status_text>
      <order_track_trace_reference/>
      <order_date_preferred_delivery>2020-12-01 00:00:00</order_date_preferred_delivery>
      <order_vat_country_code>BE</order_vat_country_code>
      <customer_id>11</customer_id>
      <invoice_id>0</invoice_id>
      <order_sales_employee_id>10369</order_sales_employee_id>
      <OrderResultItems>
        <OrderResultItem>
          <order_item_is_bicycle>0</order_item_is_bicycle>
          <order_item_object_id xsi:nil="true"/>
          <order_item_barcode>$barcode</order_item_barcode>
          <order_item_quantity>-1</order_item_quantity>
          <order_item_description>SomeBatavus</order_item_description>
          <order_item_unit_price_in_vat>1021.00</order_item_unit_price_in_vat>
          <order_item_unit_discount_amount_in_vat>21.00</order_item_unit_discount_amount_in_vat>
          <order_item_vat_code>2</order_item_vat_code>
          <order_item_status_id>0</order_item_status_id>
          <order_item_status_text>Geen status</order_item_status_text>
          <order_item_line_id>1</order_item_line_id>
          <order_item_invoice_customer_id>4</order_item_invoice_customer_id>
        </OrderResultItem>
        <OrderResultItem>
          <order_item_is_bicycle>0</order_item_is_bicycle>
          <order_item_object_id xsi:nil="true"/>
          <order_item_barcode>$barcode</order_item_barcode>
          <order_item_quantity>1</order_item_quantity>
          <order_item_description>SomeBatavus</order_item_description>
          <order_item_unit_price_in_vat>1521.00</order_item_unit_price_in_vat>
          <order_item_unit_discount_amount_in_vat>21.00</order_item_unit_discount_amount_in_vat>
          <order_item_vat_code>2</order_item_vat_code>
          <order_item_status_id>0</order_item_status_id>
          <order_item_status_text>Geen status</order_item_status_text>
          <order_item_line_id>2</order_item_line_id>
          <order_item_invoice_customer_id>2</order_item_invoice_customer_id>
        </OrderResultItem>
    </ns1:OrderStatusResponse>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

## CreateOrUpdateCustomer ##

This method creates or updates an existing customer. Existing customers are matched on `customer_id`, `customer_phone`
, `customer_mobile`, `customer_reference` or `customer_email`.

```php
<?php
try {
    $client = new \SoapClient(
        'https://api.cyclesoftware.nl/app/cs/api/ecommerce/soap_2_9/?wsdl',
        [
            'trace' => true,
            'use' => SOAP_LITERAL,
            'encoding' => 'UTF-8',
        ]
    );
    $input = (object) array(
        'Authentication' => (object) array(
            'username' => 'your-username',
            'password' => 'your-password',
            'dealer_id' => '1', // store-id within account
        ),
        'customer_type_name' => '',
        'Customer' => (object)array(
            'customer_id' => 46,
            'customer_cs_customer_id' => 235238848,
            'customer_reference' => 'unique-reference-customer',
            'customer_name_prefix' => 'Dhr.',
            'customer_name_initials' => 'A',
            'customer_middle_name' => 'Van',
            'customer_last_name' => 'Name 235238848',
            'customer_postal_code' => '8448PE',
            'customer_housenumber' => '32',
            'customer_housenumber_suffix' => 'B',
            'customer_street_name' => 'Mauritslaan',
            'customer_city' => 'Heerenveen',
            'customer_phone' => '073-3030050',
            'customer_mobile' => '06-24238848',
            'customer_country_code_iso_3166' => 'NL',
            'customer_email' => 'test235238848@cyclesoftware.nl',
            'customer_newsletter' => '0',
            'customer_date_of_birth' => NULL,
            'customer_iban' => 'NL69INGB0123456789',
            'DeliveryAddress' => NULL,
        )
    );
    $result = $client->CreateOrUpdateCustomer($input);
    var_dump($result);
} catch (\SoapFault $e) {
    var_dump($e->getMessage());
}
```

> Request

```http
POST /app/cs/api/ecommerce/soap_2_9/ HTTP/1.1
Host: api.cyclesoftware.nl
Accept-encoding: gzip,deflate
Accept: text/xml
Content-type: text/xml; charset=utf-8
User-agent: SoapClient
Soapaction: "CreateOrderUpdateCustomer"
Content-length: 1648

<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope
  xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"
  xmlns:ns1="http://api.cyclesoftware.nl/app/cs/api/ecommerce/soap_2_0/">
  <SOAP-ENV:Body>
    <ns1:CreateOrUpdateCustomerRequest>
      <Authentication>
        <username>your-username</username>
        <password>your-password</password>
        <dealer_id>1</dealer_id>
      </Authentication>
      <Customer>
        <customer_type_name>Lease-maatschappij</customer_type_name>
        <customer_cs_customer_id>235238848</customer_cs_customer_id>
        <customer_reference>unique-reference-customer</customer_reference>
        <customer_name_prefix>Dhr.</customer_name_prefix>
        <customer_name_initials>A</customer_name_initials>
        <customer_middle_name>Van</customer_middle_name>
        <customer_last_name>Name 235238848</customer_last_name>
        <customer_postal_code>8448PE</customer_postal_code>
        <customer_housenumber>32</customer_housenumber>
        <customer_housenumber_suffix>B</customer_housenumber_suffix>
        <customer_street_name>Mauritslaan</customer_street_name>
        <customer_city>Heerenveen</customer_city>
        <customer_phone>073-1234567</customer_phone>
        <customer_mobile>06-124235335</customer_mobile>
        <customer_country_code_iso_3166>NL</customer_country_code_iso_3166>
        <customer_email>test235238848@cyclesoftware.nl</customer_email>
        <customer_newsletter>0</customer_newsletter>
        <customer_date_of_birth/>
        <customer_iban>NL69INGB0123456789</customer_iban>
      </Customer>
    </ns1:CreateOrUpdateCustomerRequest>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>


HTTP/1.1 200
Content-type: application/xml; charset=utf-8
Content-length: 1448

<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope
  xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"
  xmlns:ns1="http://api.cyclesoftware.nl/app/cs/api/ecommerce/soap_2_0/">
  <SOAP-ENV:Body>
    <ns1:CreateOrUpdateCustomerResponse>
      <is_new_customer>false</is_new_customer>
      <Customer>
        <customer_cs_customer_id>235238848</customer_cs_customer_id>
        <customer_reference>REF46</customer_reference>
        <customer_name_prefix>Dhr.</customer_name_prefix>
        <customer_name_initials>A</customer_name_initials>
        <customer_middle_name>Van</customer_middle_name>
        <customer_last_name>Name 235238848</customer_last_name>
        <customer_postal_code>8448PE</customer_postal_code>
        <customer_housenumber>32</customer_housenumber>
        <customer_housenumber_suffix>B</customer_housenumber_suffix>
        <customer_street_name>Mauritslaan</customer_street_name>
        <customer_city>Heerenveen</customer_city>
        <customer_phone></customer_phone>
        <customer_mobile>0733030050</customer_mobile>
        <customer_country_code_iso_3166>NL</customer_country_code_iso_3166>
        <customer_email>test235238848@cyclesoftware.nl</customer_email>
        <customer_newsletter>0</customer_newsletter>
        <customer_date_of_birth/>
        <customer_iban></customer_iban>
      </Customer>
    </ns1:CreateOrUpdateCustomerResponse>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```
