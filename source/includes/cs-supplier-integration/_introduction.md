# Introduction #

Welcome to the CycleSoftware Supplier integration documentation. In this documentation we will outline the different components which CycleSoftware can integrate to facilitate supplier services within CycleSoftware.

## Definitions ##

- CycleSoftware: POS application
- Supplier: the articles supplier to a store
- Store: the dealer/customer of the supplier and user of CycleSoftware

## Overview ##

As as supplier for bicycle stores you can integrate with CycleSoftware by offering a set of webservices or files.
CycleSoftware will integrate the services and act as a client to the supplier server.

The integration consists of the following topics:

* Article information <i class="label label-info">required</i>
* Stock indication - nett purchase prices
* Order creation
* Dropshipment order creation
* Open order items
* Packing lists
* Spare parts

<aside class="notice">
  You can contact <a href="mailto:support@cyclesoftware.nl">support</a> for more information
</aside>

## Authentication ##

Every store in CycleSoftware can setup it's credentials for communication to the supplier. For example a customer number or a combination of username+password.

To enhance the onboarding process we can setup an e-mail address. When a store wants to integrate you'll receive an e-mail with the onboarding request for a specific store.

## Examples ##

In this documentation you'll find examples. This is just to illustrate which requests and responses are integrated. It is not necessary to use the same field names or structure.

We support a wide range of different integration content types:

- XML
- JSON
- REST
- SOAP
- CSV
