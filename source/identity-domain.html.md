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
Customer Dashboard is a place that a user can go to view activities associated with the use of their Digital Identity in relation to interactions within the Identity Hub. A version Customer dashboard is already developed and hosted on a internal only server. This feature is to provide external facing capability on "identity.gov.au" domain name. 

The following domains are needed to support externalizing this website. 
|S.No | Env Name | URL                           | Visibility | Status |
|:---:|:--------:|-------------------------------|------------|:------:|
||| *Development*                                                      |
|1.   | DEV 0    | https://dev.identity.gov.au   | Internal   | Design |
|2.   | DEV 1    | https://dev1.identity.gov.au  | Internal   | Design |
|3.   | DEV 2    | https://dev2.identity.gov.au  | Internal   | Design |
|4.   | DEV 3    | https://dev3.identity.gov.au  | Internal   | Design |
||| *Test*                                                             |
|5.   | TEST 0   | https://test.identity.gov.au  | External   | Design |
|6.   | TEST 1   | https://test1.identity.gov.au | Internal   | Design |
|7.   | TEST 2   | https://test2.identity.gov.au | Internal   | Design |
|8.   | TEST 3   | https://test3.identity.gov.au | External   | Design |
||| *Pre Production*                                                   |
|9.   | PST      | https://pst.identity.gov.au   | Internal   | Design |
||| *On-boarding*                                                      |
|10.  | ONB      | https://onb.identity.gov.au   | External   | Design |
||| *Production*                                                       |
|11.  | PROD     | https://identity.gov.au       | External   | Design |

## <a id="STAFF_SUPPORT_TOOL"></a>Staff Support Tool

The following domains are needed to support externalizing the  website. 
|S.No | Env Name | URL                           | Visibility | Status |
|:---:|:--------:|-------------------------------|------------|:------:|
||| *Development*                                                      |
|1.   | DEV 0    | https://dev.support.identity.gov.au   | Internal   | Design |
|2.   | DEV 1    | https://dev1.support.identity.gov.au  | Internal   | Design |
|3.   | DEV 2    | https://dev2.support.identity.gov.au  | Internal   | Design |
|4.   | DEV 3    | https://dev3.support.identity.gov.au  | Internal   | Design |
||| *Test*                                                             |
|5.   | TEST 0   | https://test.support.identity.gov.au  | External   | Design |
|6.   | TEST 1   | https://test1.support.identity.gov.au | Internal   | Design |
|7.   | TEST 2   | https://test2.support.identity.gov.au | Internal   | Design |
|8.   | TEST 3   | https://test3.support.identity.gov.au | External   | Design |
||| *Pre Production*                                                   |
|9.   | PST      | https://pst.support.identity.gov.au   | Internal   | Design |
||| *On-boarding*                                                      |
|10.  | ONB      | https://onb.support.identity.gov.au   | External   | Design |
||| *Production*                                                       |
|11.  | PROD     | https://support.identity.gov.au       | External   | Design |

## <a id="IDENTITY_HUB_MIGRATION"></a>Identity Hub migration
## <a id="DTA_WEB_REDIRECT"></a>DTA Identity redirection 
