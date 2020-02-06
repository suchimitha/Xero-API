---
layout: default
title: Update Xero Contact
parent: Contact Operations
nav_order: 2
---

# Update Xero Contact
To Update a Xero Contact pass the values to Accountwrapper along with contactId (Xero identifier) and assign it to request.xeroContact and then call the method BreadwinnerAPI.call().

## sample code 

```scss
try{
	bw_xero_api02.BreadwinnerAPI.RequestObject req = new  bw_xero_api02.BreadwinnerAPI.RequestObject();	
	List<bw_xero_api02.AccountWrapper> xeroContactsList = new List<bw_xero_api02.AccountWrapper>();
	bw_xero_api02.AccountWrapper xeroContact = new bw_xero_api02.AccountWrapper();
	xeroContact.name='MY5 NAME Test Create -'; 
	xeroContact.contactId ='3f5873c9-0faf-4ca4-9c0d-140c59636d0e'; //Required		
	xeroContactsList.add(xeroContact);            
	req.xeroContact = xeroContactsList;

	bw_xero_api02.BreadwinnerAPI.ResponseObject res =  bw_xero_api02.BreadwinnerAPI.call('updateContact', req);
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