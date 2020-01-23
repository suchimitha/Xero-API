---
layout: default
title: Update Purchase Order
parent: Invoice Operations
nav_order: 8
---

# Update Purchase Order

To Update purchase Order pass the values to Invoice wrapper along with PurchaseorderId (Xero identifier) and assign it to request.xeroInvoice and then call the method BreadwinnerAPI.call().

## Sample Code

```scss
try{
    bw_xero_api01.BreadwinnerAPI.RequestObject req = new  bw_xero_api01.BreadwinnerAPI.RequestObject();
    bw_xero_api01.Invoice xi = new bw_xero_api01.Invoice ();
    xi.PurchaseorderId = '5eac31f6-a05f-4a84-b3aa-47154c82afca'; // Requried
    xi.DueDate = string.valueof(system.today()+30);
    bw_xero_api01.Invoice.LineItemWrapper li = new bw_xero_api01.Invoice.LineItemWrapper();
    li.ItemCode = ''; li.Description ='li desc';li.UnitAmount=500;li.Quantity=3;li.AccountCode='200';
    list<bw_xero_api01.Invoice.LineItemWrapper> lineitems = new list<bw_xero_api01.Invoice.LineItemWrapper>();
    lineitems.add(li);
    xi.LineItems = lineitems;
    xi.ClientId = '39efa556-8dda-4c81-83d3-a631e59eb6d3';
    req.xeroInvoice= xi;


    bw_xero_api01.BreadwinnerAPI.ResponseObject res =  bw_xero_api01.BreadwinnerAPI.call('updatePurchaseOrder', req);
    if(res.errors.size()>0){
        for(bw_xero_api01.BreadwinnerAPI.Error er :res.errors){
            System.debug(er); 
        }
    }
    system.debug('Updated PO' +res.XeroInvoice);
}catch(Exception ex){
    System.debug('Exception occurred while creating customers in Stripe.'+ex.getStackTraceString());
}
```