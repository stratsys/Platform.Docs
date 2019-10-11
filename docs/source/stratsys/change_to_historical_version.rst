Change to historical version
============================

When changing from database NOT migrated to platform (Stratsys version >= 7.1)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
To other database migrated to platform
---------------------------------------
User is simply redirected to the other database, if user does not exist in other database but auto provisioning is enabled in other database then user is provisioned automatically and will have access to other database. (User might also have to authenticate for the tenant)

To other database NOT migrated to platform
------------------------------------------
Works exactly as before.

When changing from database NOT migrated to platform (Stratsys version < 7.1)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
To other database migrated to platform
---------------------------------------
User will see an error dialog when trying to change to other database

To other database NOT migrated to platform
------------------------------------------
Works exactly as before.

When changing from database migrated to platform 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
To other database migrated to platform
--------------------------------------
User is simply redirected to the other database, if user does not exist in other database but auto provisioning is enabled in other database then user is provisioned automatically and will have access to other database

To other database NOT migrated to platform
------------------------------------------
Works as previously, user is logged into other database if user exists in other database.