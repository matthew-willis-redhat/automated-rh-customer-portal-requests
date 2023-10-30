Red Hat OpenShift Client Tools Install
=========

Install Red Hat OpenShift Client tools

Requirements
------------

Elevated permissions on host

Role Variables
--------------

|Variable||
|:---|:---|
|openshift_client_version| Ex: "4.14.0"|
|openshift_client_filename| Ex: openshift-client-linux.tar.gz|
|openshift_client_tmp_dir|Ex: "/tmp/ocp-client"|
|openshift_client_bin_dir|Ex: "/usr/local/bin/"|

Example Playbook
----------------

    ---
    - name: Install Red Hat OpenShift Client Tools
      hosts: localhost
      connection: local
      gather_facts: false

      vars:
        openshift_client_version: "4.14.0"
        openshift_client_filename: "openshift-client-linux.tar.gz"
        openshift_client_tmp_dir: "/tmp/ocp-client"
        openshift_client_bin_dir: "/usr/local/bin/"

      tasks:
        - name: "[INCLUDE ROLE] - Red Hat OpenShift Client Tools Install"
          ansible.builtin.include_role:
            name: redhat-openshift-client-tools-install

    ...

License
-------

BSD

Author Information
------------------

[Matt Willis](https://github.com/matthew-willis-redhat)
