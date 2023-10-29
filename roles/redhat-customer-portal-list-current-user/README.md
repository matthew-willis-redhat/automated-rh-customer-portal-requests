Red Hat Customer Portal List Current User
=========

List current user from SSO on Red Hat Customer Portal. When using the associated `redhat_customer_portal_token`, your account name will be the result.

Requirements
------------

`redhat_customer_portal_token` variable needs to be defined. To generate an offline token, visit the [API Tokens page](https://access.redhat.com/management/api) and click the Generate Token button. Remember to properly secure this variable, as this token is associated with your account.

Role Variables
--------------

N/A

Example Playbook
----------------

    ---
    - name: List Red Hat Customer Support Current User
      hosts: localhost
      connection: local
      gather_facts: false

      vars:
        redhat_customer_portal_token:
          - *GENERATED_NUMBER_FROM_RED_HAT_OFFLINE_TOKEN*

      tasks:
        - name: "[INCLUDE ROLE] - Red Hat Customer Portal Authentication"
          ansible.builtin.include_role:
            name: redhat-customer-portal-authentication
        - name: "[INCLUDE ROLE] - Red Hat Customer Portal List Current User"
          ansible.builtin.include_role:
            name: redhat-customer-portal-list-current-user
    ...

License
-------

BSD

Author Information
------------------

[Matt Willis](https://github.com/matthew-willis-redhat)
