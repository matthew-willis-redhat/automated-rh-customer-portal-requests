Red Hat OpenShift Generate Must Gather
=========

Generate `must-gather` for Red Hat OpenShift cluster using `oc adm must-gather` command.

Requirements
------------

OpenShift Client tools must be installed prior to running `oc adm must-gather` command. The role will attempt to install openshift-client tools if it's not found locally on operating system.

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

      tasks:
        - name: "[INCLUDE ROLE] - Red Hat OpenShift Generate Must Gather"
          ansible.builtin.include_role:
            name: redhat-openshift-generate-must-gather
    ...

License
-------

BSD

Author Information
------------------

[Matt Willis](https://github.com/matthew-willis-redhat)
