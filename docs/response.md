---
layout: default
title: Response
nav_order: 2
---

# Response
{: .no_toc }

This method allows users to retrieve the data of a Xero Contact/Invoice/Bill/PurchaseOrder.


### ResponseObject - Class
When we call “BreadwinnerAPI.call()” method, User would get the response in the form of BreadwinnerAPI.ResponseObject. It consists of the following variables.<br/>

### Status: 
It is of type String, which represents the Response/Status code of the request returned by Xero. <br/>
E.g: ‘200’ - OK (Successful API call) <br/>
Click [here](https://developer.xero.com/documentation/api/http-response-codes) for more Status codes, and it's descriptions.

### xeroContacts
It is of type List<AccountWrapper>, which contains the created Xero Contact(s) data along with Xero unique record Id.<br/> 
```yaml
List<bw_xero_api02.AccountWrapper> xeroContactsList = Response.xeroContacts
```

### xeroInvoices
It is of type List<Invoice>, which contains the created Xero Invoice(s) data along with Xero unique record Id.<br/>
```yaml
List<bw_xero_api02.Invoice> xeroInvoices = Response.XeroInvoices
```

### Errors
It is of type “BreadwinnerAPI.Error” class. All the Errors that are reported by Xero or by Salesforce.

Error class contains the following variables:
<ul>
<li><b>type</b>: The type of error returned. One of api_connection_error, api_error, authentication_error, idempotency_error, invalid_request_error, rate_limit_error, validation_exception. e.t.c.,</li>
<li><b>message</b>: Represents the Error.</li>
<li><b>code</b>: For some errors that could be handled programmatically, a short string indicating the error code reported.</li>
<li><b>description</b>: Represents the extra info regarding the error or exception.</li>
</ul>

```yaml
message=REQUIRED_FIELD_MISSING: name, message=Enter the Xero customer name. param=xeroContact.name
```