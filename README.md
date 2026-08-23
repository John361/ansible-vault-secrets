# Ansible Vault Secrets
Ansible role to deploy the [main project](https://github.com/John361/vault-secrets)

## Ansible Galaxy
[Link](https://galaxy.ansible.com/ui/repo/published/john361/ansible_vault_secrets/)

## Build and deploy
```shell
source .venv/bin/activate
ansible-galaxy collection build
ansible-galaxy collection publish john361-ansible_vault_secrets-[version].tar.gz --token changeme
```
