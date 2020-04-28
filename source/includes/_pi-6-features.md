# PI6 Features

##The PI-6 will incorporate the following features:</br>

| Feature # | Feature Description    | Design Required       | MDT | Comments              |
|--------|---------|------------|---------|---------------------------|
| [MAP-9](http://jira-prod.csda.gov.au/browse/MAP-9)   | myGov On Boarding Environment| No | Magical Staff | NONE 
| [MAP-13](http://jira-prod.csda.gov.au/browse/MAP-13) | Connection of Digital Identity to myGov Account via myGov | [Yes](#MAP13) | Dragons, Magical Staff |  	
| [MAP-15](http://jira-prod.csda.gov.au/browse/MAP-15) | myAged Care move to DoH| No | Magical Staff | Carried forward from PI-5 (scheduled for Nov 23rd release)
| [MAP-16](http://jira-prod.csda.gov.au/browse/MAP-16) | Complete Abandoned myGov Integration Flow | [Yes](#MAP16) | Dragons, Magical Staff | Sequence diagrams have been attached to the respective user stories in JIRA [MI-181](http://jira-prod.csda.gov.au/browse/MI-181), [MI-182](http://jira-prod.csda.gov.au/browse/MI-182), [MI-183](http://jira-prod.csda.gov.au/browse/MI-183)
| [MAP-17](http://jira-prod.csda.gov.au/browse/MAP-17) | myGov Access App Enhancements | No | Magical Staff | NONE 
| [MAP-20](http://jira-prod.csda.gov.au/browse/MAP-20) | Identity Resolution in the Ecosystem | [Yes](#MAP20) | Mushrooms | NONE 
| [MAP-22](http://jira-prod.csda.gov.au/browse/MAP-22) | Improve Error Handling experience in myGov Integration Flow | No |  Dragons | NONE 	
| [MAP-34](http://jira-prod.csda.gov.au/browse/MAP-34) | Department of Health: Bonded Programs On-boarding to myGov | No | Magical Staff | Inbox / NAC services are not in scope for the Nov 23rd release, however they might be in scope for the Feb 2020 release so we need to create and provide TEST/PROD .pfx certs accordingly
| [MAP-37](http://jira-prod.csda.gov.au/browse/MAP-37) | ISAM DMZ Move	| No | Magical Staff | NONE 
| [MAP-40](http://jira-prod.csda.gov.au/browse/MAP-40) | Turn on Inbox and Tell Us Once for VICSRO | No | Magical Staff | Carried forward from PI-5  (scheduled for Nov 23rd release)
| [MAP-43](http://jira-prod.csda.gov.au/browse/MAP-43) | myGov Linking Tool links to Process Direct | [Yes](#MAP43) | Magical Staff | NONE 
| [MAP-47](http://jira-prod.csda.gov.au/browse/MAP-47) | Remove redundant logging to free up server space	| No | Magical Staff | NONE 
| [MAP-50](http://jira-prod.csda.gov.au/browse/MAP-50) | Remove ConnectedID code | No | Magical Staff | NONE 
| [MAP-51](http://jira-prod.csda.gov.au/browse/MAP-51) | Log myGov user session attributes | No | Magical Staff | NONE
| [MAP-53](http://jira-prod.csda.gov.au/browse/MAP-53) | Masking of Message ID header of emails sent from myGov | No | Magical Staff | NONE 
| [MAP-54](http://jira-prod.csda.gov.au/browse/MAP-54) | Exchange to forget user consent | [Yes](#MAP54) | Dragons | Stretch goal
| [MAP-62](http://jira-prod.csda.gov.au/browse/MAP-62) | Provision Australia Post to the Exchange Production Environment | No | Mushrooms| NONE 
| [MAP-65](http://jira-prod.csda.gov.au/browse/MAP-65) | DHS AusKey Decommissioning | No | Magical Staff | NONE 
| [MAP-67](http://jira-prod.csda.gov.au/browse/MAP-67) | Extend logic in Exchange to evaluate assurance levels (acr_claim)| No | Dragons | NONE 


## MAP 13 - Connection of Digital Identity to myGov Account via myGov
<a id="MAP13"></a>
This feature enables the User to connect their myGov account to their Digital Identity from an authenticated myGov session, and also allow the user to sign-in to the myGov portal using their Digital Identity.

- Appropriate validation will be performed in the myGov code to ensure that connection to Digital Identity MUST only occur if the assurance level meets the minimum requirement of IP2 + CL2.

- Once the User successfully connects their myGov account to Digital Identity, the existing session in myGov is stepped-up from their myGov credential to Digital Identity credential upon the user returning to an authenticated myGov portal.

- Four new DB tables (specified below) will be created by the myGov Developers as part of this feature to ensure that the User’s Digital Identity information is stored in separate DB tables.

  - **MGV_PROF_DIGITAL_IDENTITY**  - This table stores profile information for an associated digital identity.
  - **MGV_PROF_DIGITAL_IDENTITY_HIST** – History of digital identity profile  entries – similar to  profile history table.
  - **MGV_BANNER_REF** -   This table stores information pertaining to types of banners and properties associated.
  - **MGV_BANNER** – This table stores user interaction with banner types.

- For Feb 2020 release (MVP), we need to ensure that even though a User has already connected their myGov account to their Digital Identity, their existing myGov Profile information MUST be used for the Tell-Us-Once and Linking services, NOT their Digital Identity profile details.

- The  following schema change is required to the existing **RetrieveMyGovAgencyInfo** service to add an optional Boolean attribute to determine the User’s Digital Identity connected status.
The value of this attribute will be used to determine from which table the User’s profile information should be retrieved to be displayed on the User’s myGov home page. 
If the Boolean is set to True then the profile information should be retrieved from the new **MGV_PROF_DIGITAL_IDENTITY** table, OR ELSE the existing myGov User Profile table.

Click [here](/images/map-13/retrieve-agency-info-response-schema-change.png) to view the diagram at full size.

Click [here] (http://svn-alm-prod.csda.gov.au/svn/CSI/ServiceArtefacts/trunk/ESBRelease2/schema/mygov/authenticationhub/accountlink/messages/v20170513/mygov.authenticationhub.accountlink.messages.v20170513.xsd) for the modified Schema file in the SOAPE SVN Repository. 

![myGov Retrieve Agency Info Response schema change](/images/map-13/retrieve-agency-info-response-schema-change.png)


## MAP 16 - Complete Abandoned myGov Integration Flow
<a id="MAP16"></a>

This feature allows a user, who had previously commenced the process of linking their digital identity to myGov and not completed to be able to return and complete the process.

- No SSO (myGov account not connected to Digital Identity) JIRA [MI-181](http://jira-prod.csda.gov.au/browse/MI-181)
    - Scenario 1: (Existing myGov - No Exchange - No SSO)
	Click [here](/images/map-16/ExistingmyGov-NoExchange-NoSSO.png) to view the diagram at full size or get the PDF [here](/bin/map-16/ExistingmyGov-NoExchange-NoSSO.pdf)

	- Scenario 2: (No myGov - No Exchange - No SSO)
	Click [here](/images/map-16/NomyGov-NoExchange-NoSSO.png) to view the diagram at full size or get the PDF [here](/bin/map-16/NomyGov-NoExchange-NoSSO.pdf)
	
- No SSO (myGov account connected to Digital Identity) JIRA [MI-182](http://jira-prod.csda.gov.au/browse/MI-182)
	- Scenario 1: (Existing myGov - Connected to Exchange - No SSO)
	Click [here](/images/map-16/ExistingmyGov-ConnectedtoExchange-NoSSO.png) to view the diagram at full size or get the PDF [here](/bin/map-16/ExistingmyGov-ConnectedtoExchange-NoSSO.pdf)
	
- Active SSO session (mygov_linked claim) JIRA [MI-183](http://jira-prod.csda.gov.au/browse/MI-183)
	- Scenario 1: (Existing myGov - No Exchange - SSO available)
	Click [here](/images/map-16/ExistingmyGov-NoExchange-SSOavailable.png) to view the diagram at full size or get the PDF [here](/bin/map-16/ExistingmyGov-NoExchange-SSOavailable.pdf)
	
	- Scenario 2: (No myGov - No Exchange - SSO available)
	Click [here](/images/map-16/NomyGov-NoExchange-SSOavailable.png) to view the diagram at full size or get the PDF [here](/bin/map-16/NomyGov-NoExchange-SSOavailable.pdf)
	
	- Scenario 3: (Existing myGov - Connected to Exchange - SSO available)
	Click [here](/images/map-16/ExistingmyGov-ConnectedtoExchange-SSOavailable.png) to view the diagram at full size or get the PDF [here](/bin/map-16/ExistingmyGov-ConnectedtoExchange-SSOavailable.pdf)

The myGov OpenAPI spec which includes the below changes required as part of this feature has been documented [here](https://digital-services.pages-gitlab.csda.gov.au/architecture/mygov/api-user-account/#mygov-user-account-api)
<br>(a) modified <b>/v1/authenticator/verify</b> to return the Customer's email address or link identifier (MBUN) for the given qualified subject attribute.
<br>(b) defined a new version (v2) for <b>/accounts/links</b> as part of an orchestration API for creating OR updating the Customer's myGov profile in myGov along with creation of a new myGov RP Account Link for a given relying party.

## MAP 20 - Identity Resolution
<a id="MAP20"></a>
This diagram depicts the relationships present within the Exchange Customer Aggregate Root.

Click [here](/images/ExchangeCustomerAggRoot.png) to view the diagram at full size.

![Exchange Customer Aggregate Root Diagram](/images/ExchangeCustomerAggRoot.png)

- Sequence diagrams:

	- Scenario 1: (New Customer - New RP - New IDP - New myGov)
	Click [here](/images/map-20/NewCustomer-NewRP-NewIDP-NewmyGov.png) to view the diagram at full size or get the PDF [here](/bin/map-20/NewCustomer-NewRP-NewIDP-NewmyGov.pdf)
	
	- Scenario 2: (Existing Customer - New RP - New IDP - Existing myGov)
	Click [here](/images/map-20/ExistingCustomer-NewRP-NewIDP-ExistingmyGov.png) to view the diagram at full size or get the PDF [here](/bin/map-20/ExistingCustomer-NewRP-NewIDP-ExistingmyGov.pdf)
	
	- Scenario 3: (Existing Customer - Existing RP - New IDP - Existing myGov)
	Click [here](/images/map-20/ExistingCustomer-ExistingRP-NewIDP-ExistingmyGov.png) to view the diagram at full size or get the PDF [here](/bin/map-20/ExistingCustomer-ExistingRP-NewIDP-ExistingmyGov.pdf)


## MAP 43 - Agency Customer Link API 
<a id="MAP43"></a>
The JETT train feature 12.4 proposes to move the Confirmation of Identity guided procedure into Process Direct. In addition to this, the myGov Linking Tool will also be moved to Process Direct as Identity and Authentication transactions are seen as the same thing to Service Delivery staff. 

MaGIC will enable the myGov linking tool to integrate with Process Direct, however no updates to the functionality of the myGov linking tool itself will be made.

myGov to expose the below 3 API's to Process Direct, which will be consumed via the SAP PI/PO Integration platform:
<br>(a) Read Q&A set (retrieve PORO information and Eligibility rating stored against a Customer’s record)
<br>(b) Calculate Registration Rating
<br>(c) Generate Activation Code

The Agency Customer Link OpenAPI spec has been documented [here](https://gitlab.csda.gov.au/digital-services/architecture/portfolio/api-ext-agency-customer-link/blob/master/openapi/openapi.yaml).
<br>The API documentation is located [here](https://digital-services.pages-gitlab.csda.gov.au/architecture/portfolio/api-ext-agency-customer-link/#agency-customer-link-api).

An existing service [ClientAgencyCustomerService.java](http://svn-alm-prod.csda.gov.au/svn/ITSEC/Portfolio/portfolio-enterprise/trunk/portfolio-business-client/src/main/java/au/gov/portfolio/itsecurity/agncycust/application/client/service/ClientAgencyCustomerService.java) is available which already includes a large part of the functionality required by the API.  This should be extended to support the API.

A new (skinny) WAR artifact should be added to the portfolio-enterprise EAR project which exposes the agency-customer-link REST API.

## MAP 54 - Manage Consent and IdP selection 
<a id="MAP54"></a>
- (+) denotes a new component. 
- (*) denotes an updated component. 

### Component Diagram

Click [here](/images/IdHubComponentsDiagram.png) to view the diagram at full size or get the PDF [here](/bin/IdHubComponentsDiagram.pdf).

![Component Diagram](/images/IdHubComponentsDiagram.png)

### Identity Hub Authorisation Server (*)

Individuals will authenticate via the Identity Hub Auth Server in order to access the [Identity Hub Customer Platform](#UI_IH_CUSTMGMT_PLATFORM) in order to manage their consent rules amongst other things.

The [Identity Hub Customer Platform](#UI_IH_CUSTMGMT_PLATFORM) will be registered as Public OAUTH Client/RP with scopes `identityhub_customer_platform_read` and `identityhub_customer_platform_write`.

The Identity Hub Authorisation Servers MUST support the following [OIDC](#OIDC) and [OAUTH2](#OAUTH2) standards-based functionality:

- Public OAUTH Clients
    - This is required to support the Identity Hub Customer Platform (SPA) as a Public Client.
- Proof Key for Code Exchange [PKCE](#PKCE)
    - This is required to support Single Page Applications (SPA) Public Clients.
- A well-Known configuration Endpoint /.well-known/openid-configuration (or equivalent URL).
- Public Clients MUST use the Authorisation Code flow in order to receive Access Tokens and ID Tokens.
- Front-Channel Logout described under [OIDCFC](#OIDCFC).
- RP iframe for Session Management as described under [OIDCSESS](#OIDCSESS).
- Access Tokens as JWTs.

Authorisation Servers SHALL NOT support the following functionality:

- The Implicit flow MUST NOT be supported.
- Public Clients SHALL NOT receive Refresh Tokens.

### Identity Hub Customer Platform (+)

Identity Hub customers will be able to manage their consent rules and instances via this platform which will hosted on a seperate (sub) domain which customers may find through external means like a Google search.

This component will be developed as an Angular single page application and registerd an OIDC Relying Party on the Identity Hub Authorisation Server.  Please note that the rules that apply to TDIF RPs do not apply to this client although they are both registered as OIDC RPs.

Angular Components will be developed (or existing open source packages leveraged) to provide the following OIDC-related functionality:

- Proof Key for Code Exchange [PCKE](#PKCE).
- Front-Channel Logout described under [OIDCFC](#OIDCFC).
- RP iframe for Session Management as described under [OIDCSESS](#OIDCSESS).

### API Gateway (+)

The API Gateway will host and protect external-facing REST APIs available to the Identity Hub Customer Platform.  It must validate and unpack JWT Access Tokens (and relevant scopes) issued by the Identity Hub Authorisation Server and propagate the associated subject identifier to the downstream internal APIs. 

### Identity Hub Customer Platform API (+)

The API for this feature has been documented [here](https://digital-services.pages-gitlab.csda.gov.au/architecture/govpass/api-idhub-customer-platform).

### Domain (*)

This diagram depicts the relationships present within the Consent Permission Aggregate Root.

Click [here](/images/ExchangeConsentPermissionAggRoot.png) to view the diagram at full size.

![Exchange Consent Permission Aggregate Root Diagram](/images/ExchangeConsentPermissionAggRoot.png)
