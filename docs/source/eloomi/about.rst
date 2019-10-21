Eloomi - Stratsys integration
=====================

How does the integration work?
^^^^^^^^
* Eloomi e-learning is embedded within an iframe ('Stratsys external page') inside Stratsys web application. This url is manually added in `administration->menu->external pages`
* Url: https://stratsys.eloomi.com/stratsys/login?company_code=[companycode]
* Eloomi uses the companycode supplied in the URL above to access Stratsys IdP with the correct CompanyCode
* User signs into Eloomi with SSO by StratsysIdentityServer and using authorization code flow. A client for Eloomi is configured in platform developers and administrated by us
* If the user doesn't already exists in Eloomi, the user is created and assigned to a department in Eloomi that corresponds to the companycode in Stratsys

Eloomi "backbone domain"
^^^^^^^^
* "Single database-ish"
* `Customer` somewhat comparable to customer/tenant in our new Platform. It is what it sounds like and exists at https://[customer].eloomi.com
* Stratsys is a customer in Eloomi application
* A `customer` have one or many `departments`. A company code in Stratsys maps to a `department` in Eloomi
* A user belongs to a customer *BUT* there is also a unique constraint for e-mail which strongly hints at a single database as well as data isolation per customer does *NOT* include users (likely) or there is simply a constraint design flaw (less likely?)
* Stratsys is considered a "social login" in the same way as facebook, google etc
* However Stratsys architectural design is NOT the same as facebook, google etc. Instead every companycode should optimally be it's OWN social login the way user ids, usernames and e-mails are validated/stored internally and exposed publicly
* A user in Eloomi can have one or several "social logins" as connected logins. Both Stratsys and Facebook may exist at the same time
* A user in Eloomi can set a user password even if this is restricted in Stratsys for this specific company code and regulated through a signed contract between Stratsys and customer
* Question: If a user entity is NOT data isolated per tenant it suggests there might be a security exploit that a malicious user may be able to somehow gain access to user login for another customer. Does such a risk exist?
* Logout from Stratsys does NOT trigger logout in Eloomi

Pseudo code flow
^^^^^^^^
* Attempt to fetch the user from remote stateless connection.
* If it can’t fetch the user, it’ll redirect back to the login page
* Attempt to find an already connected user, based on the Remote UserID (Which is a unique id from their REST API)
* If successful:
* We update the users email, in case it changed
* We set the “last-login” to now
* We manually log in the user found.
* We redirect to the dashboard
* If not successful
* Attempt to find a user in eloomi with the remote user’s email.
* If a user exists with that email in eloomi.
* Create a connection to the eloomi-user and remote-user
* Manually log in of the user
* Redirect to the dashboard
* If that also fails, and no users in eloomi exists with the remote user’s email.
* Check if auto-create-users is allowed (it is for Stratsys)
* Sanity check for the email could be deleted or similar.
* Create a new eloomi user, with the information from the remote-user.
* Create/Find department based on “company_code”
* Add the user to that department
* Activate the user
* Create a connection between user and remote user
* Log in the user
* Redirect to dashboard
* If all in step #2 and #3 fails, it will redirect to the login page.

Environments
^^^^^^^^
* Stratsys production database: eloomitest, https://www.stratsys.se/eloomitest
* Eloomi production environment found at https://stratsys.eloomi.test
* Eloomi has a (non public) test instance found at https://stratsys.eloomi.test
* https://stratsys.eloomi.test/stratsys/login?company_code=eloomitest
* https://stratsys.eloomi.com/stratsys/login?company_code=eloomitest