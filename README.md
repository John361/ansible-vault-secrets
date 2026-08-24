# Ansible Vault Secrets
Ansible role for deploying [Vault Secrets](https://github.com/John361/vault-secrets) at scale.

## Overview
This Ansible collection provides a robust, automated way to deploy the Vault Secrets application across multiple servers simultaneously. Whether you're managing a handful of machines or an entire infrastructure, this role handles the heavy lifting of installation, configuration, and service management.

## Key Features
- ***Mass Deployment:*** Deploy to hundreds of servers with a single playbook execution
- ***Fully Configurable:*** Customize every aspect of the deployment via variables
- ***Idempotent:*** Safe to run multiple times; only applies necessary changes
- ***Multi-Platform:*** Supports major Linux distributions (Debian, Ubuntu)
- ***Secure by Design:*** Follows security best practices for secret management
- ***Open Source:*** AGPL v3 licensed, community-driven development

## Installation
### From Ansible Galaxy (Recommended)
```shell
ansible-galaxy collection install john361.ansible_vault_secrets
```

### From GitHub
```shell
git clone https://github.com/John361/ansible-vault-secrets.git
ansible-galaxy collection build
ansible-galaxy collection install john361-ansible_vault_secrets-*.tar.gz
```

### Requirements
- Ansible >= 2.17
- Python >= 3.14
- Target Systems: Linux (Debian/Ubuntu)

## Quick start
### Basic usage
Create a playbook `deploy-vault.yml`:
```yaml
- name: Deploy Vault Secrets
  hosts: all
  become: yes
  roles:
    - john361.ansible_vault_secrets
  vars:
    vault_address: "http://localhost:8200"
    vault_username: "admin"
    vault_password: "changeme"
    vault_mount_path: "my-kv"
```
Run the playbook:
```shell
ansible-playbook -i inventory.yml deploy-vault.yml
```

## Configuration Variables
Check `roles/vault_secrets/meta/argument_specs.yml`.

## CI/CD and release process
This project uses GitHub Actions for automated testing and deployment. Every tagged release triggers an automatic workflow that:
1. Runs linters and syntax checks
2. Executes test playbooks against multiple distributions
3. Builds the collection package
4. Publishes the new version to ***Ansible Galaxy***


### Publishing a New Version
```shell
# Update version in galaxy.yml
# Commit and push changes

git tag -a v1.0.0 -m "Release v1.0.0"
git push origin v1.0.0
```
The GitHub Action will automatically handle the Galaxy publication.

## Testing
### Local testing with Molecule
```shell
cd roles/vault_secrets
uv run molecule test
```

## Development Setup
```shell
git clone https://github.com/John361/ansible-vault-secrets.git
cd ansible-vault-secrets
uv sync
```
