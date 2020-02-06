---
layout: default
title: Create Xero Contact
parent: Contact Operations
nav_order: 1
---

# Create Xero Contact

## sample code 

To create a Xero Contact, pass the values to Accountwrapper and assign it to request.xeroContact and then call the method BreadwinnerAPI.call().

```scss
try{
	bw_xero_api02.BreadwinnerAPI.RequestObject req = new  bw_xero_api02.BreadwinnerAPI.RequestObject();	
	List<bw_xero_api02.AccountWrapper> xeroContactsList = new List<bw_xero_api02.AccountWrapper>();
	bw_xero_api02.AccountWrapper xeroContact = new bw_xero_api02.AccountWrapper();
	xeroContact.name='MY5 NAME Test Create -'; 
	xeroContactsList.add(xeroContact);            
	req.xeroContact = xeroContactsList;

	bw_xero_api02.BreadwinnerAPI.ResponseObject res =  bw_xero_api02.BreadwinnerAPI.call('createContact', req);
	if(res.errors.size()>0){
		for(bw_xero_api02.BreadwinnerAPI.Error er :res.errors){
			System.debug(er); 
		}
	}
	system.debug('created customer' +res.xeroContacts);
}catch(Exception ex){
	System.debug('Exception occurred while creating customers in Xero.'+ex.getStackTraceString());
}
```
