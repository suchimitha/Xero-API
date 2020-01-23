---
layout: default
title: Contact Operations
nav_order: 5
has_children: true
permalink: docs/CustomerOperations
---

# Contact Operations


The following is required to create or update a contact

| Field  | Type                          | Description |
|:----------|:-------------------------------------|
| Name *    | String | Full name of contact/organisation (max length = 255), Requried  |
| FirstName | String | First name of contact person (max length = 255)                 |
| LastName  | String | Last name of contact person (max length = 255)              |
| EmailAddress  | String | Email address of contact person (umlauts not supported) (max length = 255)             |
| TaxNumber | String | Tax number of contact - this is also known as the ABN (Australia), GST Number (New Zealand), VAT Number (UK) or Tax ID Number (US and global) in the Xero UI depending on which regionalized version of Xero you are using (max length = 50)                |
| AccountsReceivableTaxType      | String | Default tax type used for contact on AR invoices              |
| `PaymentTerms`      | PaymentTermWrapper | The default payment terms for the contact - see  PaymentTermWrapper fields below             |
| BillingAttentionTo      | String | max length = 255              |
| BillingStreet      | String | max length = 500              |
| BillingCity       | String | max length = 255              |
| BillingState      | String | max length = 255              |
| BillingCountry      | String | max length = 50, [A-Z], [a-z] only              |
| BillingPostalCode      | String | max length = 50             |
| Phone      |        String | Phone number of contact       |
| ContactID      | String | Xero identifier , requries while updating            |


| PaymentTermWrapper Fields  | Type                          |
|:----------|:-------------------------------------|
| `Sales`      | BillsOrSalesWrapper   |

| BillsOrSalesWrapper Fields  | Type |Description| 
|:----------|:-------------------------------------|
| Day       |   Integer | |
| Type       | String | Payment Terms (DAYSAFTERBILLDATE, DAYSAFTERBILLMONTH, OFCURRENTMONTH, OFFOLLOWINGMONTH)  |
