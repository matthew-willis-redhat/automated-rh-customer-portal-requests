Red Hat Customer Portal Create Case
=========

Create a Red Hat Customer Support case.

Requirements
------------

`redhat_customer_portal_token` variable needs to be defined. To generate an offline token, visit the [API Tokens page](https://access.redhat.com/management/api) and click the Generate Token button. Remember to properly secure this variable, as this token is associated with your account.

Role Variables
--------------

|Variable||
|:---|:---|
|ocp_cluster_id|This will be provided from redhat-openshift-cluster-information role|
|ocp_cluster_version|This will be provided from redhat-openshift-cluster-information role|
|redhat_customer_support_case_number|Red Hat Customer Support case number|
|redhat_case_product|Ex: "OpenShift Container Platform"|
|redhat_case_product_version|Ex: "4.13", Red Hat Case Product vesioning only supports Major/Minor.|
|redhat_case_summary|Ex: "Test Case Title"|
|redhat_case_description|Ex: "This is a test description"|
|redhat_case_severity|<ul><li>4 (Low)</li><li>3 (Normal)</li><li>2 (High)</li><li>1 (Urgent)</li>|

Example Playbook
----------------

    ---
    - name: Create Red Hat Customer Support Case on Red Hat Customer Portal
      hosts: localhost
      connection: local
      gather_facts: false

      vars:
        redhat_customer_portal_token:
          - *GENERATED_NUMBER_FROM_RED_HAT_OFFLINE_TOKEN*        
        redhat_case_product: "OpenShift Container Platform"
        redhat_case_product_version: "4.13" 
        redhat_case_summary: "Test Case"
        redhat_case_description: "This is a test"
        redhat_case_severity: "4 (Low)"

      tasks:
        - name: "[INCLUDE ROLE] - Red Hat Customer Portal Authentication"
          ansible.builtin.include_role:
            name: redhat-customer-portal-authentication

        - name: "[INCLUDE ROLE] - Red Hat Customer Portal Create Case"
          ansible.builtin.include_role:
            name: redhat-customer-portal-create-case
    ...

License
-------

BSD

Author Information
------------------

[Matt Willis](https://github.com/matthew-willis-redhat)
