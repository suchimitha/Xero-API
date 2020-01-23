---
layout: default
title: Create Invoice
parent: Invoice Operations
nav_order: 1
---

# Create Invoice

## Sample Code


To create an Invoice pass the values to Invoice wrapper and assign it to request.xeroInvoice and then call the method BreadwinnerAPI.call(). Here Customer (ClientId (Xero Contact Id)) is requried. 

```scss
try{
	bw_xero_api01.BreadwinnerAPI.RequestObject req = new  bw_xero_api01.BreadwinnerAPI.RequestObject();	
	bw_xero_api01.Invoice xi = new bw_xero_api01.Invoice ();
	xi.InvoiceNumber = 'inv-123';
	xi.DueDate = string.valueof(system.today());
	bw_xero_api01.Invoice.LineItemWrapper li = new bw_xero_api01.Invoice.LineItemWrapper();
	li.ItemCode = ''; li.Description ='li desc'; li.AccountCode='200';li.UnitAmount=300;li.Quantity=3;
	list<bw_xero_api01.Invoice.LineItemWrapper> lineitems = new list<bw_xero_api01.Invoice.LineItemWrapper>();
	lineitems.add(li);
	xi.LineItems = lineitems;
	xi.ClientId = '39efa556-8dda-4c81-83d3-a631e59eb6d3';
	req.xeroInvoice= xi;
	bw_xero_api01.BreadwinnerAPI.ResponseObject res =  bw_xero_api01.BreadwinnerAPI.call('createInvoice', req);
	if(res.errors.size()>0){
		for(bw_xero_api01.BreadwinnerAPI.Error er :res.errors){
			System.debug(er); 
		}
	}
	system.debug('created Invoice' +res.xeroInvoice );
}catch(Exception ex){
	System.debug('Exception occurred while creating customers in Xero.'+ex.getStackTraceString());
}
```