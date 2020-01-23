---
layout: default
title: Response
nav_order: 2
---

# Response
{: .no_toc }

This method allows users to retrieve stuff.


### ResponseObject - Class
When we call “BreadwinnerAPI.call()” method, User would get the response in the form of ResponseObject wrapper. It consists of following variables.<br/>

### Status: 
It’s a string, which represents the Response Code/status code of the request. <br/>
Ex: ‘200’ - for success Response. Click [here](https://developer.xero.com/documentation/api/http-response-codes) for more Status codes information.

### xeroCustomer:
It’s XeroCustomer wrapper instance which contains created Xero Customer data along with Xero Id.<br/>
Ex: bw_xero_api01.AccountWrapper xCustomer = Response.xeroCustomer;

### xeroInvoice:
It’s Xero Invoice wrapper instance which contains created Xero Invoice data along with Xero Id. <br/>
Ex: bw_xero_api01.Invoice xInvoices = Response.XeroInvoice

### xeroCustomers:
It's a List of Xero Customers wrapper. 
Ex: List<bw_xero_api01.AccountWrapper> xCustomers = Response.xeroCustomers

### xeroInvoices :
It's a List of Xero Invoices wrapper.
Ex: List<bw_xero_api01.Invoice> xInvoices = Response.XeroInvoices

### rawResponse:
It's a raw response from Xero. 

### Errors:
It is a list of instances of the “Error” class. You can understand the reason for issues while interacting with Xero based on the error type returned.

Error class contains the following variables.
<ul>
<li><b>type</b>: The type of error returned. One of api_connection_error, api_error, authentication_error, card_error, idempotency_error, invalid_request_error, or rate_limit_error.</li>
<li><b>message</b>: Represents the Error.</li>
<li><b>code</b>: For some errors that could be handled programmatically, a short string indicating the error code reported.</li>
<li><b>description</b>: Represents the extra info regarding the error or exception.</li>
</ul>
Ex: message=REQUIRED_FIELD_MISSING : name, message=Enter the Xero customer name. param=XeroCustomer.name