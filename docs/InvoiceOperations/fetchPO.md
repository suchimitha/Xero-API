---
layout: default
title: Fetch Purchase Orders
parent: Invoice Operations
nav_order: 9
---

# Fetch Purchase Orders

To get/fetch the Purchase Orders, pass the parameters to request.options variable and then call the method BreadwinnerAPI.call(). This method returns a list of Invoice wrapper records (xeroInvoices).

## Sample Code

Optional parameters to fetch Purchase Order(s):
purchaseOrderID, purchaseOrderNumber, where, orderBy, pageNumber, modifiedAfter.


```scss
try{
    bw_xero_api02.BreadwinnerAPI.RequestObject req = new  bw_xero_api02.BreadwinnerAPI.RequestObject();
    req.options.put('page','1');

    bw_xero_api02.BreadwinnerAPI.ResponseObject res =  bw_xero_api02.BreadwinnerAPI.call('fetchPurchaseOrders', req);
    if(res.errors.size()>0){
        for(bw_xero_api02.BreadwinnerAPI.Error er :res.errors){
            System.debug(er); 
        }
    }
    system.debug('Purchase Orders '+res.xeroInvoices);
}catch(Exception ex){
    System.debug('Exception occurred while creating customers in Stripe.'+ex.getStackTraceString());
}
```