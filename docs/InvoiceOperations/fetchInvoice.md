---
layout: default
title: Fetch Invoice
parent: Invoice Operations
nav_order: 3
---

# Fetch Invoice

To get/fetch the Invoices, pass the parameters to request.Options variabele and then call the method BreadwinnerAPI.call(). This method returns a map of Invoice  wrapper records (xeroIdInvoiceMap).

## Sample Code

Optional parameters to fetch Invoice(s):
InvoiceID, InvoiceNumber, where, orderby, pagenumber, modifiedafter.


```scss
try{
    bw_xero_api01.BreadwinnerAPI.RequestObject req = new  bw_xero_api01.BreadwinnerAPI.RequestObject();
    req.options.put('pagenumber','1');

    bw_xero_api01.BreadwinnerAPI.ResponseObject res =  bw_xero_api01.BreadwinnerAPI.call('fetchInvoice', req);
    if(res.errors.size()>0){
        for(bw_xero_api01.BreadwinnerAPI.Error er :res.errors){
            System.debug(er); 
        }
    }
    system.debug('Invoices '+res.xeroIdInvoiceMap);
}catch(Exception ex){
    System.debug('Exception occurred while creating customers in Stripe.'+ex.getStackTraceString());
}
```