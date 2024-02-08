# Article information #

As supplier you'll share article information with CycleSoftware in order to make articles known to the dealer. CycleSoftware will index the data once for all our customers with gross purchase prices.

The supplier will provide a webservice or FTP location with a fixed file-format with up-to-date article information. The data will be indexed twice every week.

## Import templates ##

If you are unable to provide the article data trough a webservice or ftp it is possible to send them by e-mail to us this will uassually be imported within 10 days.

Dutch: data@cyclesoftware.nl

Belgium: data@cyclesoftware.be

France: data@cyclesoftware.fr

You can use or example import template witch you can download in your language.

[Download in English](https://s01.cyclesoftware.nl/app/supplier/import/template/download/en/)

[Download in Dutch](https://s01.cyclesoftware.nl/app/supplier/import/template/download/nl/)

[Download in French](https://s01.cyclesoftware.nl/app/supplier/import/template/download/fr/)

[Download in German](https://s01.cyclesoftware.nl/app/supplier/import/template/download/de/)

We can import it like this for a maximum of 2 times a year, if you need it to be more frequent please contact us for the options.
## Parts & Accessories ##
For parts & accessories the following attributes are suggested to be available in the file or webservice:

-	Article number *
-	EAN / Barcode *
-	Brand name *
-	Model name *
-	Short description (POS) *
- Long description
-	Main group name *
-	Sub group name
-	Recommended Retail Price (including VAT)
-	Purchase price (excluding VAT) *
-	Package quantity (how many consumer goods within one pacakage)
-	Order quantity
-	Minimal order quantity
-	URL to image
-	Color *
-	Size
-	Other properties we might be able to index.

Attributes marked with * are mandatory

## Bicycles ##
For bicycles the following attributes are suggested to be available in the file or webservice:

- Article number *
- EAN / Barcode
- Brand name *
- Model name *
- Short description (POS) *
- Main group name (e.g. Race, City, Mountainbike) *
- Sub group name
- Frame type (Ladies, Gents, Boys, Girls, Uni)
- Frame height in cm
- Frame height description (e.g. L)
- Brand gears	
- Model gears	
- Gear count
- Brand brakes rear
- Model brakes rear
- Brand brakes front
- Model brakes front
- Wheelsize (inch)
- Color *
- Model year *
- Purchase price (ex vat) *
- Recommended retail price (ex vat)
- URL to image
- Gross weight
- Nett weight
- Long description
- Is electric bike (yes / no) *
- Battery included in price (yes / no)  **
- Battery options  
- Other properties we might be able to index.

Attributes marked with * are mandatory
** When electricbike is yes battery included is mandatory

# Stock indication #
To provide supplier stock information in CycleSoftware we are able to connect using webservices or by indexing a text file. The following information is adviced:

-	Article number
-	Stock indication
-	First delivery date
-	Quantity available
-	Nett purchase price (only in webservices)

For webservices a service supporting multiple requests accepting multiple  article numbers at once is preferred for efficiency.

## Example webservice ##

> Example HTTP request

```http
POST /supplier/api/stock/ HTTP/1.1
Host: api.supplier.com
Accept: application/json
Content-type: application/json; charset=utf-8

{
  "CustomerNumber": "1111111",
  "Articles": [
    {"ArticleNumber": "ArtNo1111"},		
    {"ArticleNumber": "ArtNo2222"},
    {"ArticleNumber": "ArtNo3333"},
    {"ArticleNumber": "ArtNo4444"}
  ]
}
```

> Example HTTP response

```http
HTTP/1.1 200 
Content-type: application/json
Content-length: 776

{
	"Articles": [
		{
			"ArticleNumber": "ArtNo1111",
			"EAN": "8733723823239",
			"StockIndication": "AVAILABLE",
			"StockQuantity": 20,
			"DeliveryDate": "2020-09-19",
			"NettPurchasePrice": 68.99	
		},		
		{
			"ArticleNumber": "ArtNo2222",
			"EAN": "873272382029",
			"StockIndication": "UNAVAILABLE",
			"StockQuantity": 0,
			"DeliveryDate": "2020-10-19",
			"NettPurchasePrice": 323.00		
		},		
		{
			"ArticleNumber": "ArtNo3333",
			"EAN": "873272382029",
			"StockIndication": "INCOURANT",
			"StockQuantity": 0,
			"DeliveryDate": null,
			"NettPurchasePrice": 2122.00	
		},	
		{
			"ArticleNumber": "ArtNo4444",
			"EAN": null,
			"StockIndication": "UNKNOWN_ARTICLE",
			"StockQuantity": null,
			"DeliveryDate": null,
			"NettPurchasePrice": null		
		}
	]
}
```

# Order creation #

Transmitting orders can be achieved using webservices or uploading text files. When text files are used we normally upload them to the suppliers’ FTP server.

Input (multiple):

-	Article number
-	Quantity
-	Reference

Output:

-	Order ID
- Result per line

## Order creation ##

> Example HTTP request

```http
POST /supplier/api/create/order/ HTTP/1.1
Host: api.supplier.com
Accept: application/json
Content-type: application/json; charset=utf-8

{
  "CustomerNumber": "1111111",
  "OrderReference": "CS1010",
  "Dropshipment": false,
  "Remarks": "description",
  "DeliveryAddress": null,
  "Items": [
    {
		  "ArticleNumber": "ART1",
		  "Quantity": 1,
		  "ItemReference": "CS1010-1"
	  },
	  {
		  "ArticleNumber": "ART2",
		  "Quantity": 2,
		  "ItemReference": "CS1010-2"
	  }
    ]
}
```

> Example HTTP response

```http
HTTP/1.1 200 
Content-type: application/json
Content-length: 484

{
  "CustomerNumber": "1111111",
  "OrderReference": "CS1010",
  "OrderNumber": "10000",
  "Items": [
    {
		  "ArticleNumber": "ART1",
		  "EAN": "87123445843",
		  "OrderedQuantity": 1,
		  "ItemReference": "CS1010-1"
	  },
	  {
		  "ArticleNumber": "ART2",
		  "EAN": "87123445843",
		  "OrderedQuantity": 2,
		  "ItemReference": "CS1010-2"
	  },
	  {
		  "EAN": null,
		  "ArticleNumber": "ART2",
		  "Error": "Unknown article or incourant",
		  "OrderedQuantity": 0
	  }
    ]
}
```

## Dropshipment order creation ##

Dropshipments are orders which will be delivered at the consumers' address. It is a variant for the Order Creation service which will include the delivery address.

> Example HTTP request

```http
POST /supplier/api/create/order-dropshipment/ HTTP/1.1
Host: api.supplier.com
Accept: application/json
Content-type: application/json; charset=utf-8

{
  "CustomerNumber": "1111111",
  "OrderReference": "CS1010",
  "Dropshipment": true,
  "Remarks": "description",
  "DeliveryAddress": {
	  "Name": "Drosphipment Naam",
	  "Street": "Afleverstraat",
	  "HouseNumber": "1",
	  "HouseNumberPostfix": "c",
	  "ZipCode": "5388GM",
	  "City": "Nistelrode",
	  "CountryCode": "NL",
	  "Email": "voorbeeld@cyclesoftware.nl",
	  "Phone": "+3173030050"
  },
  "Items": [
    {
		  "ArticleNumber": "ART1",
		  "Quantity": 1,
		  "ItemReference": "CS1010-1"
	  },
	  {
		  "ArticleNumber": "ART2",
		  "Quantity": 2,
		  "ItemReference": "CS1010-2"
	  }
    ]
}
```

# Open order items #

In many situations the store pre-ordered bicycles. 
To provide correct stock information to the dealer it is advised to provide a service where the open order items can be retrieved.

In addition it is advised to provide a service where the remarks for a specific item can be retrieved.

Normally the open-order-items endpoint will provide all open items, but if possible a filter with "article number" 

- Article number

## Get open order items ##

Get a list of open order items

> Example HTTP request 

```http
GET /supplier/api/open-order-items/ HTTP/1.1
Host: api.supplier.com
Accept: application/json
Content-type: application/json; charset=utf-8

```

> Example HTTP response

```http
HTTP/1.1 200 
Content-type: application/json
Content-length: 1853

[
  {
    "LastModifiedAt": "2021-06-01 12:00:00",
    "OrderNumber": 12345679,
    "OrderItemNumber": 1,
    "ArticleNumber": "ABC10000",
    "EAN": "8712345678901",
    "Status": "open",
    "Quantity": 1,
    "QuantityShipped": 0,
    "PackinglistNumber": null,
    "Remarks": "Remark by dealer",
    "IsMarkedSoldToCustomer": true,
    "ExpectDeliveryDate": "2021-06-28",
    "DesiredDeliveryDate": "2021-06-01"
  },
  {
    "LastModifiedAt": "2021-06-01 13:00:00",
    "OrderNumber": 12345679,
    "OrderItemNumber": 2,
    "ArticleNumber": "ABC10000",
    "EAN": "8712345678901",
    "Status": "in_transit",
    "Quantity": 1,
    "QuantityShipped": 1,
    "PackinglistNumber": "222222222",
    "Remarks": "Remark by dealer",
    "IsMarkedSoldToCustomer": false,
    "ExpectDeliveryDate": "2021-06-28",
    "DesiredDeliveryDate": null
  }
]
```

## Updating a comment ##

Updates a comment for a specific open order item

> Example HTTP request

```http
POST /supplier/api/open-order-items/12345679/1/comment/ HTTP/1.1
Host: api.supplier.com
Accept: application/json
Content-type: application/json; charset=utf-8

{
    "OrderNumber": 12345679,
    "OrderItemNumber": 1,
    "Remarks": "new remark",
    "IsMarkedSoldToCustomer": true,
    "DesiredDeliveryDate": "2021-06-28"
}

```

> Example HTTP response

```http
HTTP/1.1 200 
Content-type: application/json
Content-length: 49

{
    "error": false,
    "error_message": null
}
```

# Packing lists #
Packinglists are downloaded using webservices based on a packinglist number.

The output consists of the following fields:

-	Quantity *
-	Purchase price (important for correct margin registration) *
-	Description *
-	Article number *
-	EAN / Barcode *
-	Reference (given in the order service)
-	Order ID (result of order service)
-	Frame number
-	Serial number
-	Battery number
- Lock number
- Key number
- Engine number

<p>Attributes marked with * are mandatory</p>

## Example webservice ##

This is an example of a request for a packinglist and the response with the information.

> Example HTTP request

```http
POST /supplier/api/packinglist/ HTTP/1.1
Host: api.supplier.com
Accept: application/json
Content-type: application/json; charset=utf-8

{
  "CustomerNumber": "1111111",
  "PackinglistNumber": "22222222"
}
```

> Example HTTP response

```http
HTTP/1.1 200 
Content-type: application/json
Content-length: 800

{
  "CustomerNumber": "1111111",
  "PackinglistNumber": "22222222",
  "Items": [
    {
		  "Barcode": "87123445843",
		  "ArticleNumber": "ART1",
		  "Description": "Description of the article",
		  "OrderedQuantity": 1,
		  "DeliveredQuantity": 1,
		  "Backorder": 0,
		  "ItemReference": "CS1010-1",
		  "OrderNumber": "1212122",
		  "PurchasePrice": 99.95,
		  "FrameNumber": "Frame211212",
		  "BatteryNumber": "Battery212121"
	  },
	  {
		  "Barcode": "87123445843",
		  "ArticleNumber": "ART2",
		  "Description": "Description of the article",
		  "OrderedQuantity": 2,
		  "DeliveredQuantity": 1,
		  "Backorder": 1,
		  "ItemReference": "CS1010-2"
		  "OrderNumber": "1212122",
		  "PurchasePrice": 99.95,
		  "FrameNumber": "Frame2112123",
		  "BatteryNumber": "Battery21212123"
	  }
    ]
}
```

# Spare parts #
Get a list of spare parts for a specific bike

Input: 

-	Frame number or article number

Output (list of):

- Group/section (e.g. brakes)
- Article number
- Description
- Purchase price

## Example webservice ##

> Example HTTP request

```http
POST /supplier/api/spareparts/ HTTP/1.1
Host: api.supplier.com
Accept: application/json
Content-type: application/json; charset=utf-8

{
  "ArticleNumber": "04507783",
	"FrameNumber": null
}
```

> Example HTTP response

```http
HTTP/1.1 200 
Content-type: application/json
Content-length: 1853

{
    "ArticleNumber": "04507783",
    "items": [
        [
            {
                "GroupDescription": "E-bike componenten",
                "SparePartArticleNumber": "64622045",
                "EAN": "87832823823",
                "Quantity": 1,
                "Description": "EBP WIEL V 28 ION MMU2 V2 33NM APP ST 650MM RIG ZI",
                "ArticleNumberOEM": null,
                "NettPurchasePrice": 222.99
            },
            {
                "GroupDescription": "Frame",
                "SparePartArticleNumber": "35135142",
                "EAN": "87832823824",
                "Quantity": 1,
                "Description": "Voorvork",
                "ArticleNumberOEM": null,
                "NettPurchasePrice": 223.99
            },
            {
                "group_description": "E-bike componenten",
                "SparePartArticleNumber": "39145603",
                "EAN": "87832823825",
                "Quantity": 1,
                "Description": "KETTINGSPANNER TMM-A V2",
                "ArticleNumberOEM": null,
                "NettPurchasePrice": 227.99
            },
            {
                "group_description": "E-bike componenten",
                "article_id": "24358017",
                "EAN": "87832823826",
                "Quantity": 1,
                "Description": "VULBUS RVS FRONTMOTOR L",
                "ArticleNumberOEM": "3823021",
                "NettPurchasePrice": 227.99
            },
            {
                "group_description": "E-bike componenten",
                "article_id": "29111490",
                "EAN": "87832823827",
                "Quantity": 1,
                "Description": "BATTERIJ PAKKET ION-300 PMU4 SERIES ZILVER",
                "ArticleNumberOEM": "3823023",
                "NettPurchasePrice": 227.99
            }
        ]
    ]
}
```
