---
layout: default
title: Update Bill
parent: Invoice Operations
nav_order: 5
---

# Update Bill

To update Bill pass the values to Invoice wrapper along with InvoiceId (Xero identifier) and assign it to request.xeroInvoice and then call the method BreadwinnerAPI.call().

## Sample Code

```scss
try{
    bw_xero_api02.BreadwinnerAPI.RequestObject req = new  bw_xero_api02.BreadwinnerAPI.RequestObject();
   	List<bw_xero_api02.Invoice> xeroInvoicesList = new List<bw_xero_api02.Invoice>();
    bw_xero_api02.Invoice xeroInvoice = new bw_xero_api02.Invoice ();
    xeroInvoice.InvoiceID = '5eac31f6-a05f-4a84-b3aa-47154c82afca'; // Required
    xeroInvoice.DueDate = string.valueof(system.today()+30);
    bw_xero_api02.Invoice.LineItemWrapper billLineItem = new bw_xero_api02.Invoice.LineItemWrapper();
    billLineItem.ItemCode = ''; 
    billLineItem.Description ='li desc';
    billLineItem.UnitAmount = 500;
    billLineItem.Quantity = 3;
    billLineItem.AccountCode = '200';
    list<bw_xero_api02.Invoice.LineItemWrapper> billLineItemsList = new list<bw_xero_api02.Invoice.LineItemWrapper>();
    billLineItemsList.add(billLineItem);
    xeroInvoice.LineItems = billLineItemsList;
    xeroInvoice.ClientId = '39efa556-8dda-4c81-83d3-a631e59eb6d3';
   	xeroInvoicesList.add(xeroInvoice);
    req.xeroInvoice = xeroInvoicesList;


    bw_xero_api02.BreadwinnerAPI.ResponseObject res =  bw_xero_api02.BreadwinnerAPI.call('updateBill', req);
    if(res.errors.size()>0){
        for(bw_xero_api02.BreadwinnerAPI.Error er :res.errors){
            System.debug(er); 
        }
    }
    system.debug('Updated Bill' +res.XeroInvoices);
}catch(Exception ex){
    System.debug('Exception occurred while creating customers in Stripe.'+ex.getStackTraceString());
}
```