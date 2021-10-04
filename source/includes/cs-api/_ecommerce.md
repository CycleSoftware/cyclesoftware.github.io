# E-commerce #

The e-commerce APIs are designed for pushing e-commerce orders to CycleSoftware.

### Authentication ###

The authentication is handled in the `Authentication` element of the SOAP requests.

| Field               | Type      | Description                                                                                                          |
|-------------------------|-----------|----------------------------------------------------------------------------------------------------------------------|
|`username`                  | string    |  API credentials username |
|`password`                  | string    |  API credentials password |
|`dealer_id`                  | string    |  Leave empty or specify the store_id or use the API-key |

***Scope(s)***

- `e-commerce`

### Definition ###

The latest definition of the WSDL specification can be found at:

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">WSDL-SOAP</i>
		<h6>/app/cs/api/ecommerce/soap_2_8/?wsdl</h6>
	</div>
</div>

## SaveOrder ##
Creates a new order in CycleSoftware

Field | Description
-- | --
`Authentication.dealer_id` | Leave 0 for default store_id based on authentication   username and password. If > 0 the value will be used to identify the store   within the account
`Order.order_vat_country_code` | Apply the VAT rates of this country code. CS will only   apply the VAT rates if enabled in account settings and if   order_ship_to_customer is true. If the VAT rates are not applied or the same   as the country of the account, it will default back to null in the   OrderStatusResponse
`Order.order_payment_method_description` | Use “psp” for payments using a Payment service Provider   (e.g. iDEAL, Bancontact etc.)
`OrderItems.OrderItem.order_item_is_bicycle` | Indicate whether this order item is a sold bicycle (0 or   1)
`OrderItems.OrderItem.order_item_supplier_order_mode` | 0: no supplier order or reservation on objects<br/>1: automatically create supplier order for this sales   order<br/>2: automatically reserve available stock objects based   on the object_id in order_item_object_id or order_item_barcode field.
`OrderItems.OrderItem.order_item_supplier_id` | When order_item_supplier_mode = 1, make the supplier   order for this supplier. Supplier IDs can be looked up in   https://api.cyclesoftware.nl/app/api/groups/
`OrderItems.OrderItem.order_item_object_id` | Reserve this specific object for this order item
`OrderItems.OrderItem.order_item_invoice_customer_id` | If supplied with integer value > 0 this order item   will be invoiced to this customer id (SplitOrder) All the customer info in   the SaveOrder should be the “rider” or “consumer”

> Request

```html
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://api.cyclesoftware.nl/app/cs/api/ecommerce/soap_2_1/">
  <SOAP-ENV:Body>
    <ns1:SaveOrderRequest>
      <Authentication>
        <username>User1</username>
        <password>Pass1</password>
        <dealer_id>0</dealer_id>
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
        <Customer>
          <customer_cs_customer_id>0</customer_cs_customer_id>
          <customer_reference>REF</customer_reference>
          <customer_name_prefix>G</customer_name_prefix>
          <customer_middle_name>van</customer_middle_name>
          <customer_last_name>Wijgergangs</customer_last_name>
          <customer_postal_code>5258 hl</customer_postal_code>
          <customer_housenumber>2</customer_housenumber>
          <customer_housenumber_suffix>B</customer_housenumber_suffix>
          <customer_street_name>Sassenheimseweg</customer_street_name>
          <customer_city>Berlicum</customer_city>
          <customer_phone>0733030050</customer_phone>
          <customer_mobile>0622903913</customer_mobile>
          <customer_country_code_iso_3166>NL</customer_country_code_iso_3166>
          <customer_email>gielwijgergangs@gmail.com</customer_email>
          <customer_newsletter>1</customer_newsletter>
          <customer_iban>NL71INGB0008871139</customer_iban>
          <customer_date_of_birth>1988-09-29</customer_date_of_birth>
          <DeliveryAddress>
            <delivery_address_use_delivery_address>1</delivery_address_use_delivery_address>
            <delivery_address_name>CycleSoftare</delivery_address_name>
            <delivery_address_street_name>Kievitsven 22</delivery_address_street_name>
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
```

> Response

```html
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

> Request

```html
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://api.cyclesoftware.nl/app/cs/api/ecommerce/soap_2_1/">
  <SOAP-ENV:Body>
    <ns1:UpdateOrderRequest>
      <Authentication>
        <username></username>
        <password></password>
        <dealer_id>0</dealer_id>
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
```

> Response

```html
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

## AddOrderItems ##

Add new order items to an existing order

> Request

```html
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://api.cyclesoftware.nl/app/cs/api/ecommerce/soap_2_1/">
  <SOAP-ENV:Body>
    <ns1:AddOrderItemsRequest>
      <Authentication>
        <username></username>
        <password></password>
        <dealer_id>0</dealer_id>
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
```

> Response

```html
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

> Example in PHP

```php
<?php
try {
    $client = new \SoapClient(
        'https://api.cyclesoftware.nl/app/cs/api/ecommerce/soap_2_8/?wsdl',
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
    $input->Authentication->dealer_id = '0';
    $input->invoice_number = '44848';
    $result = $client->GetInvoiceDocument($input);
    var_dump($result);
} catch (\SoapFault $e) {
    var_dump($e->getMessage());
}
```

> Request

```html
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://api.cyclesoftware.nl/app/cs/api/ecommerce/soap_2_0/">
  <SOAP-ENV:Body>
    <ns1:GetInvoiceDocumentRequest>
      <Authentication>
        <username>test</username>
        <password>fuji95</password>
        <dealer_id>0</dealer_id>
      </Authentication>
      <invoice_number>44848</invoice_number>
    </ns1:GetInvoiceDocumentRequest>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

> Response

```html
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

## CreateOrderUpdateCustomer ##

| Field               | Type      | Description                                                                                                          |
|-------------------------|-----------|----------------------------------------------------------------------------------------------------------------------|
|`customer_type_name`                  | string    |  One of the following: `Klant`, `Leverancier`, `E-commerce`, `Zakelijk`, `Lease-rijder`, `Lease-maatschappij`, `Werkgever` |

> Request

```html
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope
  xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"
  xmlns:ns1="http://api.cyclesoftware.nl/app/cs/api/ecommerce/soap_2_0/">
  <SOAP-ENV:Body>
    <ns1:CreateOrUpdateCustomerRequest>
      <Authentication>
        <username>test</username>
        <password>fuji95</password>
        <dealer_id>0</dealer_id>
      </Authentication>
      <Customer>
        <customer_type_name>Lease-maatschappij</customer_type_name>
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
```

> Response

```html
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
