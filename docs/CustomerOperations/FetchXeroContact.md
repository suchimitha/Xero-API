---
layout: default
title: Fetch Xero Contacts
parent: Contact Operations
nav_order: 3
---

# Fetch Xero Contacts

To get/fetch, the Xero Contact pass the parameters to request.Options variable and then call the method BreadwinnerAPI.call(). Returns a map of AccountWrapper records (xeroIdCustomerMap). 

## sample code 

Optional parameters to fetch Xero Contact(s):
ContactId, ContactNumber, where, orderby, pagenumber, modifiedafter.

```scss
try{
    bw_xero_api02.BreadwinnerAPI.RequestObject req = new  bw_xero_api02.BreadwinnerAPI.RequestObject();
    req.options.put('pagenumber','1');

    bw_xero_api02.BreadwinnerAPI.ResponseObject res =  bw_xero_api02.BreadwinnerAPI.call('fetchContacts', req);
        if(res.errors.size()>0){
            for(bw_xero_api02.BreadwinnerAPI.Error er :res.errors){
                System.debug(er); 
            }
        }
        else{
            system.debug('created customer' +res.xeroContacts);
        }
}catch(Exception ex){
    System.debug('Exception occurred while creating customers in Stripe.'+ex.getStackTraceString());
}
```