# PI8 Features

The PI-8 will incorporate the following features:

| Feature # | Feature Description    | Design Required       | MDT | Comments              |
|-----------|------------------------|-----------------------|-----|-----------------------|
| [MAP-50](http://jira-prod.csda.gov.au/browse/MAP-50)     | Removal of the 'connectedID' code from myGov| No | Magical Staff | NONE
| [MAP-193](http://jira-prod.csda.gov.au/browse/MAP-193)   | Restrict the ability to request verified documents to specific document types| No | Dragons | NONE
| [MAP-199](http://jira-prod.csda.gov.au/browse/MAP-199)   | Educational information for identity.gov.au| No | Mushrooms | NONE
| [MAP-202](http://jira-prod.csda.gov.au/browse/MAP-202)   | User Dashboard authenticated landing page| No | Mushrooms | NONE
| [MAP-218](http://jira-prod.csda.gov.au/browse/MAP-218)   | On-board the DTA mock Relying Party to onboarding environment| No | Mushrooms | NONE
| [MAP-222](http://jira-prod.csda.gov.au/browse/MAP-222)   | On-board the NDIS app to myGov MAP and enable tell us once capabilities| No | Mushrooms | NONE
| [MAP-220](http://jira-prod.csda.gov.au/browse/MAP-220)   | Updated Error message for de-duplication| No | Dragons | NONE
| [MAP-166](http://jira-prod.csda.gov.au/browse/MAP-166)   | Ability for a user to unlink a digital identity from their myGov account| No | Magical Staff | NONE
| [MAP-221](http://jira-prod.csda.gov.au/browse/MAP-221)   | Update URLs on myGov/Identity Hub that redirect from Human Services to Services Australia| No | Magical Staff and Mushrooms | NONE
| [MAP-42](http://jira-prod.csda.gov.au/browse/MAP-42)     | Connect digital identity to myGov via an authenticated member service session| [Yes](#MAP42) | Dragons | NONE
| [MAP-155](http://jira-prod.csda.gov.au/browse/MAP-155)   | Broadcast capability for myGov unauthenticated pages| [Yes](#MAP155) | Magical Staff | NONE
| [MAP-184](http://jira-prod.csda.gov.au/browse/MAP-184)   | Enhance mobile authentication pattern to accept digital identity| [Yes](#MAP184) | Magical Staff | NONE
| [MAP-185](http://jira-prod.csda.gov.au/browse/MAP-185)   | Enhance web authentication pattern to accept digital identity| [Yes](#MAP185) | Magical Staff | NONE
| [MAP-223](http://jira-prod.csda.gov.au/browse/MAP-223)   | Archiving inactive myGov accounts| [Yes](#MAP223) | Magical Staff | NONE


## MAP 42 - Connect digital identity to myGov via an authenticated member service session
<a id="MAP42"></a>
A link to the design paper needs to be pasted here once reviewed and approved by GPAG


## MAP 155 - Broadcast capability for myGov unauthenticated pages
<a id="MAP155"></a>
This feature is to implement a broadcast capability for the myGov unauthenticated sign in page.
Users would be informed of any outages to member services or upcoming changes without the requirement to sign in to myGov to receive that information.

Support staff members in the Channel Operations Facility (COF) create/submit these incident messages via the GovCMS Portal to be published on the myGov website. This is an existing process and will remain unchanged.

The current design proposal is that the myGov Landing JSP Page in the Unauthenticated space should directly initiate an API call (via the User Agent/Browser) to the 'Alert:List:Active' resource API, exposed by the GovCMS system (that sits behind an Akamai CDN cache) to retrieve a list of all active alerts that must be published on the myGov website. 

Click [here](../images/myGov frontend - GovCMS integration.png) to view the component diagram at full size.

Reference to the API specification is [here](https://content-dhs.govcms.gov.au/docs#operation/alert.list.active).


## MAP 184 - Enhance mobile authentication pattern to accept digital identity
<a id="MAP184"></a>
Embed a link to the design paper once reviewed and approved by GPAG


## MAP 185 - Enhance web authentication pattern to accept digital identity
<a id="MAP185"></a>
Embed a link to the design paper once reviewed and approved by GPAG


## MAP 223 - Archiving inactive myGov accounts
<a id="MAP223"></a>
The detailed design strategy for archiving inactive myGov accounts must be documented here.