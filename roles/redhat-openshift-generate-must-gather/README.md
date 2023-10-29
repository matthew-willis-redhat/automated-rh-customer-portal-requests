Red Hat OpenShift Generate Must Gather
=========

Generate `must-gather` for Red Hat OpenShift cluster using `oc adm must-gather` command.

Requirements
------------

OpenShift Client tools must be installed prior to running `oc adm must-gather` command. The role will attempt to install openshift-client tools if it's not found locally on operating system.

Role Variables
--------------

|Variable||
|:---|:---|
|openshift_version| Ex: "4.14.0"|
|openshift_client_filename| Ex: openshift-client-linux.tar.gz|
|openshift_client_tmp_dir|Ex: "/tmp/ocp-client"|
|openshift_client_bin_dir|Ex: "/usr/local/bin/"|

Example Playbook
----------------

    ---
    - name: List Red Hat Customer Support Current User
      hosts: localhost
      connection: local
      gather_facts: false

      vars:
        openshift_version: "4.14.0"
        openshift_client_filename: "openshift-client-linux.tar.gz"
        openshift_client_tmp_dir: "/tmp/ocp-client"
        openshift_client_bin_dir: "/usr/local/bin/"

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
