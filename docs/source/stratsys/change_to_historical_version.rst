Change to historical version
==========================

From database NOT migrated to platform -> other database NOT migrated to platform
^^^^^^^
Works exactly as before.

From database migrated to platform -> other database migrated to platform
^^^^^^
User is simply redirected to the other database, if user does not exist in other database but auto provisioning is enabled in other database then user is provisioned automatically and will have access to other database

From database migrated to platform -> other database NOT migrated to platform
^^^^^^^^^^^^^^^
Works as previously, user is logged into other database if user exists in other database.

From database NOT migrated to platform with Stratsys version >= 7.1 -> other database migrated to platform
^^^^^^^^^^^
User is simply redirected to the other database, if user does not exist in other database but auto provisioning is enabled in other database then user is provisioned automatically and will have access to other database. (User might also have to authenticate for the tenant)

From database NOT migrated to platform with Stratsys version < 7.1 -> other database migrated to platform
^^^^^^^^^^^
User will see an error dialog when trying to change to other database
