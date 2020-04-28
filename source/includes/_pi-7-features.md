# PI7 Features

The PI-7 will incorporate the following features:

| Feature # | Feature Description    | Design Required       | MDT | Comments              |
|-----------|------------------------|-----------------------|-----|-----------------------|
| [MAP-33](http://jira-prod.csda.gov.au/browse/MAP-33)     | On-board Medicare to mobile authentication pattern (MAP)| No | Mushrooms | NONE
| [MAP-72](http://jira-prod.csda.gov.au/browse/MAP-72)     | On-board National Cancer Screening Register to myGov| No | Mushrooms | NONE
| [MAP-178](http://jira-prod.csda.gov.au/browse/MAP-178)   | View my activities on user dashboard| No | Mushrooms | NONE
| [MAP-47](http://jira-prod.csda.gov.au/browse/MAP-47)     | Remove redundant logging to free up server space| No | Magical Staff | NONE
| [MAP-195](http://jira-prod.csda.gov.au/browse/MAP-195)   | Turn-Off Manage ABN Connections (MAC) from myGov| No | Magical Staff | NONE
| [MAP-203](http://jira-prod.csda.gov.au/browse/MAP-203)   | Move GSE and ITS into GITLAB| No | Magical Staff | NONE
| [MAP-180](http://jira-prod.csda.gov.au/browse/MAP-180)   | Display document information requested by the Relying Party| No | Dragons | NONE
| [MAP-181](http://jira-prod.csda.gov.au/browse/MAP-181)   | Enhancements to myGov beta sign-in page| No | Dragons | NONE
| [MAP-182](http://jira-prod.csda.gov.au/browse/MAP-182)   | myGov account management for an account that only has digital identity credentials| No | Magical Staff | NONE
| [MAP-204](http://jira-prod.csda.gov.au/browse/MAP-204)   | Disposal of expired member service messages in myGov inbox data store| [Yes](#MAP204) | Magical Staff | NONE
| [MAP-55](http://jira-prod.csda.gov.au/browse/MAP-55)     | Manage IdPs enrolled in private beta from IdPs enrolled in public beta| [Yes](#MAP55) | Mushrooms | NONE
| [MAP-210](http://jira-prod.csda.gov.au/browse/MAP-210)   | Expose myGov Inbox API to support the digital experience platform dashboard| [Yes](#MAP210) | Magical Staff | NONE
| [MAP-211](http://jira-prod.csda.gov.au/browse/MAP-211)   | Expose myGov Tell us Once API to support the digital experience platform dashboard| [Yes](#MAP211) | Magical Staff | NONE
| [MAP-198](http://jira-prod.csda.gov.au/browse/MAP-198)   | Enhancements to myGov Integration architecture design| [Yes](#MAP198) | Dragons | NONE


## MAP 204 - Disposal of expired member service messages in myGov inbox data store
<a id="MAP204"></a>
With the number of member services onboarding to Inbox function increases from time to time, the number of inbox messages in myGov Database grows rapidly. It is noted that a very large number of the inbox messages in the myGov data store are 'Expired', which has implications on storage and stability issues resulting in poor performance in myGov.

- Proposed solution:

  - Remove/Delete all expired metadata from the myGov Inbox DB table **MGV_COMM**. However prior to deletion, check for any dependencies on this table: if they do exist, the cascade delete option should be considered after exhaustive review & impact analysis.
  - As part of the MVP, manually execute the SQL DELETE command to remove expired metadata from this table (and dependent tables if any).
  - It is recommended to delete the expired data in small SQL batches rather than a one-off DELETE, to ensure there is no adverse impact on the DB.
  - Post MVP, need to work towards defining and implementing a daily batch job to automate this process.

Relevant Member services must be informed that the expired metadata, once deleted from the myGov DB, can be no longer recovered.

## MAP 55 - Manage IdPs enrolled in private beta from IdPs enrolled in public beta
<a id="MAP55"></a>
The functionality required for this feature will enable the Exchange to determine the type of enrolment a Relying Party or Identity Provider is provisioned in the Exchange (i.e. private or public enrolment). As a result, the Exchange shall prompt users the list of accredited Identity Providers supported in that enrolment.
For example if a user is participating in a public beta for a Relying Party, the Exchange would only want to display Identity Providers that are also in Public beta or that are Live.

- Proposed solution:

  - Extend the configuration of Relying Party registration details in the Exchange so that it includes an enrolment phase. This includes 'Private beta', 'Public beta' and 'Live' phases.
  - Extend the configuration of Identity Provider registration details in the Exchange so that it includes an enrolment phase. This includes 'Private beta' and 'Public beta' phases.
  - Update registered RP and IdP details in all environments from Dev to Production to include the enrolment phase.
  - Evaluate and display accredited Identity Providers that support an authentication request from a public beta RP.
  - Evaluate and display accredited Identity Providers that support an authentication request from a private beta RP.

The connected Relying Parties, Identity Providers and Attribute Providers should be classified as follows:

| Relying Party details  | Classification    |
|------------------------|-------------------|
| ATO Online (TFN) | private​
| ATO RAM | private
| DSS Grants | private
| ​USI | public
| ​myGov | private
| ​Centrelink | private
| DHS PRODA | public​
| **Identity Provider details**
| ​myGovID | public
| ​DigitalID | private
| ​myGov | ??
| **Attribute Provider details**
| ​RAM | private

## MAP 210 - Expose myGov Inbox API to support the digital experience platform dashboard
<a id="MAP210"></a>
Currently, Services Australia is in the process of developing a digital experience platform (DxP) that will deliver a proof of concept for a beta at some stage in 2020.

The DxP will utilise some of myGov capabilities and will require MaGIC to develop APIs for the Inbox so that the technical enabling team for the DxP can consume them and commence testing for their beta.

The External myGov Digital Mail OpenAPI spec is located [here](https://gitlab.csda.gov.au/digital-services/architecture/mygov/api-ext-mygov-digitalmail/blob/master/openapi/openapi.yaml).
<br>The API documentation is located [here](https://digital-services.pages-gitlab.csda.gov.au/architecture/mygov/api-ext-mygov-digitalmail/#external-mygov-digital-mail-api).


## MAP 211 - Expose myGov Tell us Once API to support the digital experience platform dashboard
<a id="MAP211"></a>
Currently, Services Australia is in the process of developing a digital experience platform (DxP) that will deliver a proof of concept for a beta at some stage in 2020.

The DxP will utilise some of myGov capabilities and will require MaGIC to develop APIs for the Tell Us Once functionality so that the technical enabling team for the DxP can consume them and commence testing for their beta.

The External myGov Tell Us Once OpenAPI spec is located [here](https://gitlab.csda.gov.au/digital-services/architecture/mygov/api-ext-mygov-tuo/blob/master/openapi/openapi.yaml).
<br>The API documentation is located [here](https://digital-services.pages-gitlab.csda.gov.au/architecture/mygov/api-ext-mygov-tuo/#external-mygov-tell-us-once-api).


## MAP 198 - Enhancements to myGov Integration architecture design
<a id="MAP198"></a>
The current design for myGov integration does not adequately account for de-duplication and utilises the myGov MBUN as that user’s pairwise identifier for linking the relying party with the exchange. This also does not account for situations where an account is already made and a link is subsequently established.

- Proposed solution:

  - **mygov_link_id** - The mygov_linked claim should be replaced with a 'mygov_link_id' claim, which will return the mygov_link_id for that user’s link between myGov and the relying party requesting the authentication. It can be requested as part of the "claims" request parameter in the Authorization Request. This claim should not initiate any user flows at the Exchange.
  - **mygov_link** - Introduce an additional value called 'mygov_link' for the User flow URL parameter, which may be requested by a Relying Party when it expects the user to undergo myGov integration. This value need not be passed to the IdP. A Relying Party may request multiple values for this URL Parameter. The 'user_flow' request parameter will hold values that indicate the desired user flow for the user at the Identity Provider and/or the Exchange. Defined values are: *sign_in, sign_up, mygov_link*.