Supported endpoints
===================

- Azure AD Sync only supports a subset of the functionality of the SCIM specification defined in SCIM 2.0 (RFC `7642 <https://datatracker.ietf.org/doc/html/rfc7642>`_, `7643 <https://datatracker.ietf.org/doc/html/rfc7643>`_, `7644 <https://datatracker.ietf.org/doc/html/rfc7644>`_).
- As a rule of thumb,  **Azure AD Sync supports the same endpoints as** `Azure <https://docs.microsoft.com/en-us/azure/active-directory/app-provisioning/use-scim-to-provision-users-and-groups#scim-protocol-requests-and-responses>`_ .
- Below is a non-exhaustive list of supported endpoints (not including all endpoints listed in Azure) and cases where our implementation differ from Azure.

+------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
| Endpoint                                                               | Comments                                                                                                               |
+========================+===============================================+========================================================================================================================+
| /Groups?excludedAttributes=members&filter=displayName eq "displayName" | *excludedAttributes* is available only for Azure compability and will be ignored. I.e. members are always excluded.    |
+------------------------+-----------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
| /Groups?filter=id eq groupId and members eq userId&attributes=id       | Used by Azure to check if a member is the last member of a group. (If true group can be removed.)                      |
+------------------------+-----------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
| /Groups                                                                | If no filter is provided, all groups (with members excluded) will be returned.                                         |
+------------------------+-----------------------------------------------+------------------------------------------------------------------------------------------------------------------------+


