---
title: MaGIC Train PI Design - Identity Domain name change
toc_footers: 
  - <a href='changelog.html'>Complete Change log</a>

includes: 

search: true

---

# MaGIC Train PI Design - Identity Domain name change
DTA and Train has decided to use *identity.gov.au* domain instead of *identityhub.my.gov.au*. Currently *identity.gov.au* domain is owned and managed by DTA. Services Australia has put in a request to CEO to transfer the domain to Services Australia and on **2020-04-01** that request has been accepted. 

This paper is to document the tasks involved to migrate the domain name and setup required mappings for various apps. At this time the plan is to use the domain name for the following 

1.  [Customer Dashboard](#CUSTOMER_DASHBOARD)
1.  [Staff support tool](#STAFF_SUPPORT_TOOL)
1.  [Identity Hub](#IDENTITY_HUB_MIGRATION)
1.  [DTA Identity Website redirection](#DTA_WEB_REDIRECT) (Not sure if needed)  

## <a id="CUSTOMER_DASHBOARD"></a>Customer Dashboard


<div hidden>

```
@startuml firstDiagram

actor Foo1
boundary Foo2
control Foo3
entity Foo4
database Foo5
collections Foo6
Foo1 -> Foo2 : To boundary
Foo1 -> Foo3 : To control2
Foo1 -> Foo4 : To entity
Foo1 -> Foo5 : To database
Foo1 -> Foo6 : To collections		
@enduml
```
![](bin\firstDiagram.svg)

</div>

## <a id="STAFF_SUPPORT_TOOL"></a>Staff Support Tool

<div hidden>

```
@startuml firstDiagram2

Alice -> Bob: Hello
Bob -> Alice: Hi!
		
@enduml

```

![](bin\firstDiagram2.svg)

</div>


## <a id="IDENTITY_HUB_MIGRATION"></a>Identity Hub migration 

## <a id="DTA_WEB_REDIRECT"></a>DTA Identity redirection 
