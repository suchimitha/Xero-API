---
layout: default
title: Create Invoice
parent: Invoice Operations
nav_order: 1
---

# Create Invoice

## Sample Code


To create an Invoice, pass the values to Invoice wrapper and assign it to request.xeroInvoice and then call the method BreadwinnerAPI.call(). Here customer ClientId (Xero Contact Id) is required.
<script src="js/jquery-1.9.1.min.js" type="text/javascript"></script>
<script src="https://code.jquery.com/ui/1.12.1/jquery-ui.min.js"></script>
<script src="https://code.jquery.com/jquery-3.4.1.min.js"></script>
<script>
function copyToClipboard(element) {
  var $temp = $("<input>");
  $("body").append($temp);
  $temp.val($(element).text()).select();
  document.execCommand("copy");
  $temp.remove();
}
</script>


<button onclick="copyToClipboard('#code')">Copy Snippet</button>
```scss
<pre id="code">
try{
	bw_xero_api02.BreadwinnerAPI.RequestObject req = new  bw_xero_api02.BreadwinnerAPI.RequestObject();	
	List<bw_xero_api02.Invoice> xeroInvoicesList = new List<bw_xero_api02.Invoice>();
	bw_xero_api02.Invoice xeroInvoice = new bw_xero_api02.Invoice ();
	xeroInvoice.InvoiceNumber = 'inv-123';
	xeroInvoice.DueDate = string.valueof(system.today());
	bw_xero_api02.Invoice.LineItemWrapper invoiceLineItem = new bw_xero_api02.Invoice.LineItemWrapper();
	invoiceLineItem.ItemCode = 'xc-123'; 
	invoiceLineItem.Description ='li desc'; 
	invoiceLineItem.AccountCode = '200';
	invoiceLineItem.UnitAmount = 300;
	invoiceLineItem.Quantity = 3;
	list<bw_xero_api02.Invoice.LineItemWrapper> invoiceLineItemsList = new list<bw_xero_api02.Invoice.LineItemWrapper>();
	invoiceLineItemsList.add(invoiceLineItem);
	xeroInvoice.LineItems = invoiceLineItemsList;
	xeroInvoice.ClientId = '39efa556-8dda-4c81-83d3-a631e59eb6d3';
	xeroInvoicesList.add(xeroInvoice);
	req.xeroInvoices = xeroInvoicesList;
	bw_xero_api02.BreadwinnerAPI.ResponseObject res =  bw_xero_api02.BreadwinnerAPI.call('createInvoice', req);
	if(res.errors.size()>0){
		for(bw_xero_api02.BreadwinnerAPI.Error er :res.errors){
			System.debug(er); 
		}
	}
	system.debug('created Invoice' +res.xeroInvoices );
}catch(Exception ex){
	System.debug('Exception occurred while creating customers in Xero.'+ex.getStackTraceString());
}
</pre>
```

