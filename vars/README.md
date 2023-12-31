# Collection Variables

Store your variables in this folder.

## Example - Create Case Variables

redhat-create-customer-support-case.yml

```yaml
---

ocp_cluster_name: 
ocp_base_domain:

# OpenShift cluster version
openshift_version: "4.12"
openshift_client_filename: openshift-client-linux.tar.gz
openshift_client_tmp_dir: "/tmp/ocp-client"
openshift_client_bin_dir: "/usr/local/bin/"

# Product Name
redhat_case_product: "OpenShift Container Platform"

# Product Version
redhat_case_product_version: "{{ openshift_version }}"

# Summary (Title) for support case
redhat_case_summary: "Test Case"

# Description for support case
redhat_case_description: "This is a test"

# Set case severity
# Case Severity Options
# 1 (Urgent)
# 2 (High)
# 3 (Normal)
# 4 (Low)
redhat_case_severity: "4 (Low)"

redhat_customer_support_case_number:
redhat_customer_support_attach_file:

redhat_customer_support_case_comment: "Adding a test comment for end-to-end automated testing."
...
```

## Example - Customer Portal Token

redhat-customer-support-token.yml

```yaml
redhat_customer_portal_token: *GENERATED_NUMBER_FROM_RED_HAT_OFFLINE_TOKEN*
```

!!!Note
    Use Ansible Vault to encrypt this file

### Encrypting personal customer portal token

Using Ansible Vault, you can encrypt sensitive information with Ansible. In this case, it's a simple command to encrypt:

#### Encrypt

```bash
ansible-vault encrypt redhat-customer-support-token.yml
```

#### Using Ansible Vault file with a Playbook

Using your protected credentials with a playbook? Just add the flag `--ask-vault-pass` to the end of your command.

```bash
ansible-playbook run-this-playbook.yml --ask-vault-pass
```

Reference the [Ansible Vault](https://docs.ansible.com/ansible/latest/vault_guide/index.html) documenation for more information.
