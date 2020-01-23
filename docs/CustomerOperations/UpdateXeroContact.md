---
layout: default
title: Update Xero Contact
parent: Contact Operations
nav_order: 2
---

# Update Xero Contact
To Update an Xero Contact pass the values to Accountwrapper along with contactId (Xero identifier) and assign it to request.xeroCustomer and then call the method BreadwinnerAPI.call().

## sample code 

```scss
try{
	bw_xero_api01.BreadwinnerAPI.RequestObject req = new  bw_xero_api01.BreadwinnerAPI.RequestObject();	
	bw_xero_api01.AccountWrapper str = new bw_xero_api01.AccountWrapper();
	str.name='MY5 NAME Test Create -'; 
	str.contactId ='tempId'; //requried		
	req.xeroCustomer = str;

	bw_xero_api01.BreadwinnerAPI.ResponseObject res =  bw_xero_api01.BreadwinnerAPI.call('updateCustomer', req);
	if(res.errors.size()>0){
		for(bw_xero_api01.BreadwinnerAPI.Error er :res.errors){
			System.debug(er); 
		}
	}
	system.debug('created customer' +res.xeroCustomer);
}catch(Exception ex){
	System.debug('Exception occurred while creating customers in Xero.'+ex.getStackTraceString());
}
```