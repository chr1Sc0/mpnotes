# Tenants
Logical container that can hold multiple applications and users. It usually hold a single customer applications.

### Permissions
Permissions needed to create tenants is "Administrator". The "Tenant Viewer" is able to see other tenants apart from the assigned tenant but obviously does not allow any modification.

### Single Sign-On
The mPulse portal login has been integrated with Akamai's Luna portal through Single Sign-On (SSO). By default mPulse will always try to authenticate against "Luna". Check  [here](https://community.akamai.com/docs/DOC-8418-mpulse-akamai-single-sign-on-migration) for more info.

Just one Single Sign On (SSO) provider can be defined per Tenant. Each Tenant has a unique SAML ID. This value needs to be crosschecked to be the same in Luna for the customer account:

1. Go to Luna portal: https://control.akamai.com
2. Navigate to "Advanced Search" and type the customer name and select "in:Accounts".
3. Once the customer account is selected, choose "Review Contracts" from the bottom choices.
4. Verify the "Account ID" value. It should match the SAML ID in mPulse.

In the tenant, the SSO integration with Luna is enabled by selecting the tick "Override SSO settings with system SSO settings"

### Properties
* **Allow Custom Dashboards:** Permits the users on the tenant creating dashboards other then system predefined.
* **External Data Sources:** This can be set to pull synthetic users metrics from other analytics tools like AppDynamics, Amazon CloudWatch, Dynatrace, etc… so these can be shown in mPulse dashboards.
* **Data Templates:** Regions you want to get the locations from. Can be overwritten at the application level.

TODO: Include other Tenant attributes that I cannot check due to restricted priviledges.

### Folders Groups
The following main folders are used to group customers tenants depending on their nature:
  1. Enterprise: Enterprise Customers
  2. POCs: Proof of Concepts (presales or deals TBA). For "POCs" where the SSO integration with Luna is disabled, users need to add the /Login to the mpulse.soasta.com/concerto URL: https://mpulse.soasta.com/concerto/Login
  3. Lite: Freemium version of mPulse. Automatically created from the mPulse website by the users. Limitations: 1 user, 1 App and 100,000 beacons / month
  4. Inactive: When a POC trial time is finished and does not realize into a sale or stops paying the subscription it's moved to this folder. The "Account Status" attribute for the tenant is set to "Suspended" or Expiration date. No user can login to the tenant once it's suspended or expiration date is past due.
