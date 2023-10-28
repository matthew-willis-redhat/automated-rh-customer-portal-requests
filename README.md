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

### 

## References

1. [Customer Portal Integration Guide
](https://access.redhat.com/documentation/en-us/red_hat_customer_portal/1/html-single/customer_portal_integration_guide/index#Authentication)
2. [Getting started with Red Hat APIs](https://access.redhat.com/articles/3626371)
3. [API - Case Management](https://access.redhat.com/management/api/case_management#/)
