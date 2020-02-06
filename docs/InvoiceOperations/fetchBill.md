---
layout: default
title: Fetch Bills
parent: Invoice Operations
nav_order: 6
---
# Fetch Bills

To get/fetch the Bills, pass the parameters to request.options variable and then call the method BreadwinnerAPI.call(). This method returns a list of Invoice wrapper records (xeroInvoices).

## Sample Code

Optional parameters to fetch Bill(s):
invoiceID, invoiceNumber, where, orderBy, pageNumber, modifiedAfter.

```scss
try{
    bw_xero_api02.BreadwinnerAPI.RequestObject req = new  bw_xero_api02.BreadwinnerAPI.RequestObject();
    //req.options.put('invoicenumber','INV-0041');
    req.options.put('pagenumber','1');

    bw_xero_api02.BreadwinnerAPI.ResponseObject res =  bw_xero_api02.BreadwinnerAPI.call('fetchBills', req);
    if(res.errors.size()>0){
        for(bw_xero_api02.BreadwinnerAPI.Error er :res.errors){
            System.debug(er); 
        }
    }
    system.debug('Bills '+res.xeroInvoices);
}catch(Exception ex){
    System.debug('Exception occurred while creating customers in Stripe.'+ex.getStackTraceString());
}
```