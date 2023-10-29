Red Hat Customer Portal Add Case Comment
=========

Add a comment to a previously created Red Hat Customer Support Case.

Requirements
------------

`redhat_customer_portal_token` variable needs to be defined. To generate an offline token, visit the [API Tokens page](https://access.redhat.com/management/api) and click the Generate Token button. Remember to properly secure this variable, as this token is associated with your account.

Role Variables
--------------

|Variable||
|:---|:---|
|redhat_customer_support_case_comment|A comment that will be added to the case|
|redhat_customer_support_case_number|Red Hat Customer Support case number|

Example Playbook
----------------

    ---
    - name: Add Comment on Support Case on Red Hat Customer Portal
      hosts: localhost
      connection: local
      gather_facts: false

      vars:
        redhat_customer_portal_token:
          - *GENERATED_NUMBER_FROM_RED_HAT_OFFLINE_TOKEN*
        redhat_customer_support_case_comment: "This is a case comment"
        redhat_customer_support_case_number: "0123456"

      tasks:
        - name: "[INCLUDE ROLE] - Red Hat Customer Portal Authentication"
          ansible.builtin.include_role:
            name: redhat-customer-portal-authentication

        - name: "[INCLUDE ROLE] - Red Hat Customer Portal Add Case Comment"
          ansible.builtin.include_role:
            name: redhat-customer-portal-add-case-comment
    ...

License
-------

BSD

Author Information
------------------

[Matt Willis](https://github.com/matthew-willis-redhat)
