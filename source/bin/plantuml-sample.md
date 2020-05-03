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
@startuml sequence_diagram
skinparam monochrome reverse 

title: <size:25>Sequence Diagram</size>

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
</div>

![](sequence_diagram.png)

## <a id="STAFF_SUPPORT_TOOL"></a>Staff Support Tool

<div hidden>

```
@startuml activity_diagram
title: <size:25>Activity Diagram</size>

(*) --> if "Some Test" then
-->[true] "activity 1"
if "" then
-> "activity 3" as a3
else
if "Other test" then
-left-> "activity 5"
else
--> "activity 6"
endif
endif
else
->[false] "activity 2"
endif
a3 --> if "last test" then
--> "activity 7"
else
-> "activity 8"
endif
@enduml
		
@enduml

```

</div>

![]( activity_diagram.png )

@startmindmap mind_map
skinparam monochrome true
title: <size:15>Use of OpenIconic</size>

+ root node
++ some first level node
+++_ second level node
+++_ another second level node
+++_ foo
+++_ bar
+++_ foobar
++ another first level node
-- Minus Node
--- Minus node 2 
--- minus node 3
---_ minus node with no box
@endmindmap

![]( mind_map.png )

@startwbs work_breakdown_structure
* Business Process Modelling WBS
** Launch the project
*** Complete Stakeholder Research
*** Initial Implementation Plan
** Design phase
*** Model of AsIs Processes Completed
**** Model of AsIs Processes Completed1
**** Model of AsIs Processes Completed2
*** Measure AsIs performance metrics
*** Identify Quick Wins
** Complete innovate phase
@endwbs

![]( work_breakdown_structure.png )

## <a id="IDENTITY_HUB_MIGRATION"></a>Identity Hub migration 

## <a id="DTA_WEB_REDIRECT"></a>DTA Identity redirection 
