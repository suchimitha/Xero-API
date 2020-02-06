---
layout: default
title: Request
nav_order: 2
---

# Request
{: .no_toc }


## Actions
It is a type of string used to define the type of action that needs to be performed. It generally accepts the following types of actions.

<ul>

<li><b>createContact</b>: Creates a Xero Contact. (includes Xero Customers and Xero Vendors)</li>
<li><b>updateContact</b>: Updates a Xero Contact. (includes Xero Customers and Xero Vendors)</li>
<li><b>fetchContacts</b>: Fetches a single Xero Contact or a list of Xero Contacts from Xero.</li>
<li><b>createInvoice</b>: Creates an Invoice in Xero.</li>
<li><b>updateInvoice</b>: Updates in Invoice in Xero.</li>
<li><b>fetchInvoices</b>: Fetches either a single Invoice or list of Invoices from Xero.</li>
<li><b>createBill</b>: Creates a Bill in Xero.</li>
<li><b>updateBill</b>: Updates a Bill in Xero.</li>
<li><b>fetchBills</b>: Fetches either a single Bill or list of Bills from Xero.</li>
<li><b>createPurchaseOrder</b>: Creates a Purchase Order (PO) in Xero.</li>
<li><b>updatePurchaseOrder</b>: Updates a Purchase Order (PO) in Xero.</li>
<li><b>fetchPurchaseOrders</b>: Fetches either a single Purchase Order or a list of Purchase Orders from Xero.</li>

</ul>

## RequestObject - Class
You have to create an Instance for RequestObject and pass to the "BreadwinnerAPI.call()” method as one of the parameters. <br/>
```yaml
BreadwinnerAPI.RequestObject request = new BreadwinnerAPI.RequestObject(); 
```

It consists of the following variables:

### 1. xeroContact
It is an instance of the AccountWrapper (Xero Contact Wrapper) class. To Create/Insert a Xero Contact, we should pass the desired values to the respective variables. For available xeroContact variables, please refer [here]({{ site.baseurl }}{% link docs/CustomerOperations/CustomerOperations.md %})
```yaml
    List<bw_xero_api02.BreadwinnerAPI.AccountWrapper> xeroContactList = new list<bw_xero_api02.BreadwinnerAPI.AccountWrapper>();
    bw_xero_api02.BreadwinnerAPI.AccountWrapper xeroContact = new bw_xero_api02.BreadwinnerAPI.AccountWrapper();
    xeroContact.name = 'Test Customer';
    xeroContactList.add(xeroContact);
    request.xeroContact = xeroContactList;
```

### 2. xeroInvoice
It is an instance of the Invoice wrapper class. To Create/Insert customer we should pass desired values to variables. For all Invoice variables you can refer [here]({{ site.baseurl }}{% link docs/InvoiceOperations/InvoiceOperations.md %}) 
```yaml
    List<bw_xero_api02.BreadwinnerAPI.Invoice> xeroInvoiceList = new list<bw_xero_api02.BreadwinnerAPI.Invoice>();
    bw_xero_api02.BreadwinnerAPI.Invoice xeroInvoice = new bw_xero_api02.BreadwinnerAPI.Invoice();
    xeroInvoice.CustomerId = 'Test Customer'; 
    xeroInvoice.description = 'desc';… 
    xeroInvoiceList.add(xeroInvoice);
    request.xeroInvoice = xeroInvoiceList;
```

### 3. options 
It is a collection of type Map (Map<String, Object>), used to pass any type of filters that to be passed in the request or any config settings that we enable.
below are the options can be used while fetching records. <br/>
    
> <b>Contacts</b>: ContactId, ContactNumber, where, PageNumber, ModifiedAfter <br/>
> <b>Invoices, Bills</b>: InvoiceNumber, InvoiceId, where, PageNumber, ModifiedAfter <br/>
> <b>PurchaseOrders</b>: PurchaseOrderNumber, PurchaseOrderID, where, PageNumber, ModifiedAfter <br/>

```yaml
request.options.put('PageNumber','1');
```
