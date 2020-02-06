---
layout: default
title: Create Purchase Order
parent: Invoice Operations
nav_order: 7
---

# Create Purchase Order

To create Purchase Order pass the values to Invoice wrapper and assign it to request. xeroInvoice and then call the method BreadwinnerAPI.call(). Here customer ClientId (Xero Contact Id) is required. 

## Sample Code

```scss
try{
	bw_xero_api02.BreadwinnerAPI.RequestObject req = new  bw_xero_api02.BreadwinnerAPI.RequestObject();	
	List<bw_xero_api02.Invoice> xeroInvoicesList = new List<bw_xero_api02.Invoice>();
	bw_xero_api02.Invoice xeroInvoice = new bw_xero_api02.Invoice ();
	xeroInvoice.DueDate = string.valueof(system.today());
	bw_xero_api02.Invoice.LineItemWrapper poLineItem = new bw_xero_api02.Invoice.LineItemWrapper();
	poLineItem.ItemCode = ''; 
	poLineItem.Description = 'li desc'; 
	poLineItem.AccountCode = '200';
	poLineItem.UnitAmount = 300;
	poLineItem.Quantity = 3;
	list<bw_xero_api02.Invoice.LineItemWrapper> poLineItemsList = new list<bw_xero_api02.Invoice.LineItemWrapper>();
	poLineItemsList.add(poLineItem);
	xeroInvoice.LineItems = poLineItemsList;
	xeroInvoice.ClientId = '39efa556-8dda-4c81-83d3-a631e59eb6d3';
	xeroInvoicesList.add(xeroInvoice);
	req.xeroInvoice = xeroInvoicesList;
	bw_xero_api02.BreadwinnerAPI.ResponseObject res =  bw_xero_api02.BreadwinnerAPI.call('createPurchaseOrder', req);
	if(res.errors.size()>0){
		for(bw_xero_api02.BreadwinnerAPI.Error er :res.errors){
			System.debug(er); 
		}
	}
	system.debug('created purchase Order' +res.XeroInvoices);
}catch(Exception ex){
	System.debug('Exception occurred while creating customers in Xero.'+ex.getStackTraceString());
}
```