Red Hat Customer Portal Authentication
=========

Generate bearer token for Red Hat Customer Support user from portal authentication token. To generate an offline token, visit the [API Tokens page](https://access.redhat.com/management/api) and click the Generate Token button

Requirements
------------

`redhat_customer_portal_token` variable needs to be defined. To generate an offline token, visit the [API Tokens page](https://access.redhat.com/management/api) and click the Generate Token button. Remember to properly secure this variable, as this token is associated with your account.

Role Variables
--------------

N/A

Example Playbook
----------------

    ---
    - name: Test Red Hat Customer Support API Authentication
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
    ...

License
-------

BSD

Author Information
------------------

[Matt Willis](https://github.com/matthew-willis-redhat)
