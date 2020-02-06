---
layout: default
title: Create Invoice
parent: Invoice Operations
nav_order: 1
---

# Create Invoice

## Sample Code
```javascript
/* Global scope: this code is executed once */
const redis = require('redis');

const host = <HOSTNAME>;
const port = <PORT>;
const password = <PASSWORD>;

...
```
{: #code-example-1}

{% if page.content contains "code" %}
<script>
<!-- clipboard.js code -->
</script>
{% endif %}


var allCodeBlocksElements = $( "code" );

allCodeBlocksElements.each(function(i) {
 	// add different id for each code block

	// target	
  var currentId = "codeblock" + (i + 1);
  $(this).attr('id', currentId);
     
  //trigger
  var clipButton = '<button class="btn" data-clipboard-target="#' + currentId + '"><img src="https://clipboardjs.com/assets/images/clippy.svg" width="13" alt="Copy to clipboard"></button>';
     $(this).after(clipButton);
  });
 
  new Clipboard('.btn');



  <script src="https://code.jquery.com/jquery-3.2.1.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/clipboard@1/dist/clipboard.min.js"></script>


<code>print("Club Nacional de Football")</code>
<br>
<code>print("is a sports institution")</code>
<br>
<code>print("from Uruguay")</code>



To create an Invoice, pass the values to Invoice wrapper and assign it to request.xeroInvoice and then call the method BreadwinnerAPI.call(). Here customer ClientId (Xero Contact Id) is required.

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

