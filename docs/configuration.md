---
layout: default
title: Request
nav_order: 2
---

# Request
{: .no_toc }


## Actions
It’s a string, used to define the type of action that needs to be performed. We are providing below types of actions.

<ul>

<li><b>createContact</b>: Creates a Xero Contact.</li>
<li><b>updateContact</b>: Updates a Xero Contact.</li>
<li><b>fetchContact</b>: Fetches a single Xero Contact or a list of Xero Contacts from Xero.</li>
<li><b>createInvoice</b> Creates an Invoice in Xero.</li>
<li><b>updateInvoice</b>: Updates in Invoice in Xero.</li>
<li><b>fetchInvoice</b>: Fetches either a single Invoice or list of Invoices from Xero.</li>
<li><b>createBill</b>: Creates a Bill in Xero.</li>
<li><b>updateBill</b>: Updates a Bill in Xero.</li>
<li><b>fetchBill</b>: Fetches either a single Bill or list of Bills from Xero.</li>
<li><b>createPurchaseOrder</b>: Creates a Purchase Order (PO) in Xero.</li>
<li><b>updatePurchaseOrder</b>: Updates a Purchase Order (PO) in Xero.</li>
<li><b>fetchPurchaseOrder</b>: Fetches either a single Purhcase Order or list of Purchase Orders from Xero.</li>

</ul>




## RequestObject - Class
You have to create an Instance for RequestObject and pass to the "BreadwinnerAPI.call()” method as one of the parameters. <br/>
RequestObject req = new RequestObject(); 

It consists of the following variables:

### 1. xeroCustomer
It is an instance of the AccountWrapper (Xero Contact Wrapper) class. To Create/Insert customer we should pass desired values to variables. For all xeroCustomer variables you can refer [here]({{ site.baseurl }}{% link docs/CustomerOperations/CustomerOperations.md %})
```yaml
Ex: bw_xero_api01.BreadwinnerAPI.AccountWrapper xContact = new bw_xero_api01.BreadwinnerAPI.AccountWrapper();
    xContact.name = 'Test Customer'; 
    req.xeroCustomer = xContactc;
```

### 2. xeroInvoice
It is an instance of the Invoice wrapper class. To Create/Insert customer we should pass desired values to variables. For all Invoice variables you can refer [here]({{ site.baseurl }}{% link docs/InvoiceOperations/InvoiceOperations.md %}) 
```yaml
Ex: bw_xero_api01.BreadwinnerAPI.Invoice inv = new bw_xero_api01.BreadwinnerAPI.Invoice();
    inv.CustomerId = 'Test Customer'; 
    inv.description = 'desc';… 
    req.xeroInvoice = inv;
```

### 3. options 
It is a collection of type Map (Map<String, Object>), used to pass any type of config settings that we enable.
    below options used for fetching records. <br/>
    
    - Contacts : ContactId, ContactNumber, where, PageNumber, ModifiedAfter
    - Invoices, Bills : InvoiceNumber, InvoiceId, where, PageNumber, ModifiedAfter
    - PurchaseOrders : PurchaseOrderNumber, PurchaseOrderID, where, PageNumber, ModifiedAfter

    
Ex: req.options.put('PageNumber','1');

