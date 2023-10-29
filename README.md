# Automate Red Hat Customer Portal Requests

Create Red Hat customer support cases using Ansible.

## Generating a new offline token

An offline token never expires as long as it is used at least **once every 30 days** and is used to create access tokens. It works as a password and allows you to continue being able to authenticate your account without having to create new refresh tokens.

Warning: Please use password management that is consistent with networking best practices. It is never safe to store any passwords or credentials in plaintext. Treat your offline token with the same security measures that you would a password to protect it against unauthorized use.

To generate an offline token, visit the [API Tokens page](https://access.redhat.com/management/api) and click the Generate Token button.

## Ansible setup

### Ansible Vault file for offline token

After generating your [offline token](#generating-a-new-offline-token), create a new file in the `vars/` directory called `redhat-customer-portal-token.yml`

Run this Ansible command to create an Ansible Vault, encrypted file.

`ansible-vault create redhat-customer-portal-token.yml`

```yaml
---
rh_customer_portal_token: *INSERT_OFFLINE_TOKEN_HERE*
...
```

!!!note

    Remember this token is **YOUR** login and should be treated as such. Be mindful to not share this file with others.

If the offline token is invalid or if the playbooks are unable to authenticate, try regenerating the token.

### Playbook Examples

#### Create Red Hat Customer Support Case for OpenShift Container Platform

```yaml
---
- name: Create Support Case on Red Hat Customer Portal
  hosts: localhost
  connection: local
  gather_facts: false

  vars_files:
    - vars/redhat-customer-portal-token.yml
    - vars/redhat-create-customer-support-case.yml

  tasks:
    - name: "[INCLUDE ROLE] - Red Hat Customer Portal Authentication"
      ansible.builtin.include_role:
        name: redhat-customer-portal-authentication

    - name: "[INCLUDE ROLE] - Red Hat Customer Portal Create Case"
      ansible.builtin.include_role:
        name: redhat-customer-portal-create-case
...
```

```bash
ansible-playbook redhat-customer-portal-create-case.yml --ask-vault-pass
```

#### Add Attachment to Red Hat Customer Support Case

```yaml
---
- name: Add Attachment to Support Case on Red Hat Customer Portal
  hosts: localhost
  connection: local
  gather_facts: false

  vars_files:
    - vars/redhat-customer-portal-token.yml
    - vars/redhat-create-customer-support-case.yml

  tasks:
    - name: "[INCLUDE ROLE] - Red Hat Customer Portal Authentication"
      ansible.builtin.include_role:
        name: redhat-customer-portal-authentication

    - name: "[INCLUDE ROLE] - Red Hat Customer Portal Add File To Case"
      ansible.builtin.include_role:
        name: redhat-customer-portal-add-file-to-case
...
```

```bash
ansible-playbook redhat-customer-portal-add-file-to-case.yml --ask-vault-pass
```

## References

1. [Customer Portal Integration Guide
](https://access.redhat.com/documentation/en-us/red_hat_customer_portal/1/html-single/customer_portal_integration_guide/index#Authentication)
2. [Getting started with Red Hat APIs](https://access.redhat.com/articles/3626371)
3. [API - Case Management](https://access.redhat.com/management/api/case_management#/)
