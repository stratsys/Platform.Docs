Create client in Platform Developers
====================================
For ADToStratsysSync to work you need to add a client in Platform Developers for the customers tenant alias. You also need to create an appSettings.json file with the customers settings. This file you should send to the customer who will then follow the installation instructions and replace the default appSettings.json provided in the ADToStratsysSync zip archive with this customized settings file.

Add client
^^^^^^^^^^
Go to https://developers.svc.stratsys.com . Choose the customers tenant alias as workspace and sign in.

Add a new Client with Grant type **Client credentials**. Name it **Platform ADToStratsysSync**.

 .. image:: images/addClient.jpg
   :width: 500
   
 .. image:: images/clientSettings.png
   :width: 500

Add scopes
^^^^^^^^^^
Add API resource scopes **Stratsys API v1 full access** and **User APIs user.readwrite**.

  .. image:: images/addScopes.png
   :width: 500
   
Add sectet
^^^^^^^^^^
Add a client secret. Remember to copy the secret after pressing Save.

  .. image:: images/addSecret.png
   :width: 500
   
Appsettings.json
^^^^^^^^^^^^^^^^
1.	Save a copy of the :download:`template.appSettings.json <./doc/template.appSettings.json>` file with the name **appSettings.json**.

2.  Open the appSettings.json file and paste in the ClientSecret you copied in the previous step. 

 .. image:: images/appSettings.png
   :width: 500
   
3.	Fill in the customers TenantId and CompanyCode

4. Copy the ClientId and paste it in the appSettings.json file.

  .. image:: images/copyClientId.png
   :width: 500

.	Send the edited appSettings.json file to the customer.
