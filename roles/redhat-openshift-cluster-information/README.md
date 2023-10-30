Red Hat OpenShift Cluster Information
=========

Capture Red Hat OpenShift cluster information using `oc get clusterversion -o jsonpath='{.items[].spec.clusterID}{"\n"}'` command.

Requirements
------------

OpenShift Client tools must be installed prior to running `oc get clusterversion` command. The role will attempt to install openshift-client tools if it's not found locally on operating system.

Role Variables
--------------

|Variable||
|:---|:---|
|ocp_cluster_id|This is the clusterID variable that gets added when running this role|
|ocp_cluster_version| Ex: "4.14.0"|
|ocp_cluster_version_short|Ex: "4.14"|

Example Playbook
----------------

    ---
    - name: List Red Hat OpenShift Cluster Information
      hosts: localhost
      connection: local
      gather_facts: false

      tasks:
        - name: "[INCLUDE ROLE] - Red Hat OpenShift Cluster Information"
          ansible.builtin.include_role:
            name: redhat-openshift-cluster-information
    ...

License
-------

BSD

Author Information
------------------

[Matt Willis](https://github.com/matthew-willis-redhat)
