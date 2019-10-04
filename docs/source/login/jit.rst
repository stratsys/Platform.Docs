.. _just-in-time-user-provisioning:

Just-in-time user provisioning
==============================

- Use *just-in-time user provisioning* to allow users logging in for the first time using single sign-on to automatically be created in the platform.
- The user is created according to the mapping made in :ref:`attribute mappings <saml2-attribute-mappings>`
- Enabled by clicking *User provisioning* and click the *Just-in-time user provisioning* checkbox.
- If the *Username* claim is not mapped, it falls back on the ``Subject.NameId``.
- *Email* falls back to *Username* if the latter is a valid e-mail address.

.. note:: Except for the fallback rules above, creation of users using user-provisioning follows the same rules as when creating user in the administration or using the api. This means that *First name* and *Last name* cannot be empty.