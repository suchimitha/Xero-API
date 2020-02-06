---
layout: default
title: Home
nav_order: 1
description: "Breadwinner Xero API is hosted on GitHub Pages."
permalink: /
---

# Breadwinner API for Xero
{: .fs-9 }


---

## Introduction
Breadwinner global API is used to communicate with Xero via Breadwinner/Salesforce. Requests & Responses are defined in such a way that you can make use of them and form the required things as per the request and get the response.

We have created two Handlers, one is for Request, and another is for Response. They are named as RequestObject and ResponseObject respectively, which are inner classes of BreadwinnerAPI.

Currently, we are providing API to create, update, and fetch operations for Xero Contacts, Invoices, Bills, and Purchase Orders from Salesforce to Xero.

Breadwinner exposes their global apex classes and methods, which can be used in the custom Apex code and design your flow. 

The following are the class and methods.

## BreadwinnerAPI Class 
This is a global class where you can access RequestObject and ResponseObject.

### Namespace
"bw_xero_api02": Use this namespace to access <i>BreadwinnerAPI's</i> classes and methods. All methods are static.

## BreadwinnerAPI Methods
The following are methods for <i>BreadwinnerAPI</i>.
- <b>call(action, request)</b><br/>
This is a global method which will return list of Customers or Invoices in the form of [BreadwinnerAPI.ResponseObject]({{ site.baseurl }}{% link docs/response.md %}).

### Signature
BreadwinnerAPI.ResponseObject call(String action, BreadwinnerAPI.RequestObject request)

### Parameters
>  - <b>Action</b>: Used to define the type of action that needs to be performed.<br/>
Type: String<br/>
E.g: createCustomer, createInvoice,… see [List of available actions]({{ site.baseurl }}{% link docs/configuration.md %})

>  - <b>Request</b>: An instance of [RequestObject]({{ site.baseurl }}{% link docs/configuration.md %}).<br/>
Type: BreadwinnerAPI.RequestObject<br/>
E.g:  BreadwinnerAPI.RequestObject request = new BreadwinnerAPI.RequestObject();

### Return Value
Type: [BreadwinnerAPI.ResponseObject]({{ site.baseurl }}{% link docs/response.md %})

### Usage
This is an synchronous method, it will make Http callouts. So, while invoking this method from a Future method, please set callout to True in the Future Annotation.<br/>
E.g: @Future(callout=true)

### BreadwinnerAPI inner classes

> - RequestObject - Class
> - ResponseObject - Class





---
