Red Hat OpenShift Validate Kube Config
=========

Validate if `~/.kube/config` or `KUBECONFIG` exists.

Requirements
------------

`~/.kube/config` must be present or `KUBECONFIG` must be a defined environment variable.

Role Variables
--------------

N/A

Example Playbook
----------------

    ---
    - name: Validate Kube Config
      hosts: localhost
      connection: local
      gather_facts: false

      tasks:
        - name: "[INCLUDE ROLE] - Red Hat OpenShift Validate Kube Config"
          ansible.builtin.include_role:
          name: redhat-openshift-validate-kube-config

    ...

License
-------

BSD

Author Information
------------------

[Matt Willis](https://github.com/matthew-willis-redhat)
