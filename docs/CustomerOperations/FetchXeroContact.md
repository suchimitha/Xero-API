---
layout: default
title: Fetch Xero Contact
parent: Contact Operations
nav_order: 3
---

# Fetch Xero Contact

To get/fetch the Xero Contcat pass the parameters to request.Options variabele and then call the method BreadwinnerAPI.call(). Returns a map of AccountWrapper records (xeroIdCustomerMap). 

## sample code 

Optional parameters to fetch Xero Contact(s):
ContactId, ContactNumber, where, orderby, pagenumber, modifiedafter.

```scss
try{
    bw_xero_api01.BreadwinnerAPI.RequestObject req = new  bw_xero_api01.BreadwinnerAPI.RequestObject();
    req.options.put('contactid','1174683a-66d1-422c-b719-30176afa06ef'); // or
    req.options.put('ContactNumber','TempNumber'); // or
    req.options.put('pagenumber','1');

    bw_xero_api01.BreadwinnerAPI.ResponseObject res =  bw_xero_api01.BreadwinnerAPI.call('fetchcustomers', req);
        if(res.errors.size()>0){
            for(bw_xero_api01.BreadwinnerAPI.Error er :res.errors){
                System.debug(er); 
            }
        }
        else{
            system.debug('created customer' +res.xeroIdCustomerMap);
        }
}catch(Exception ex){
    System.debug('Exception occurred while creating customers in Stripe.'+ex.getStackTraceString());
}
```