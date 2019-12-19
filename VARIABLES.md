# Files and Variables

A list of files within the project which the contain variables that need to be changed. The Encryption column denotes if the variable will be encrypted (tick), or stored in plaintext (blank).

## Vault Password

Ansible Vault password used to encrypt all of the following variables. This password should be stored securely for future use as it does not after project execution.

| Variable | Description | Encrypted |
| ------ | ----------- | ----------- |
| `vault_password` | The vault password used for variable encryption |  |

## aws_credentials

Credentials of the target AWS accounts to be used when provisioning new clusters. Multiple AWS environments can be supported. The name of each AWS environment must be added to the `aws_credential_list`, and the associated `access_key_id` and `secret_access_key` credentials also specified with the environment name prefixed to each:

```bash
aws_credential_list:
  - 'dev'
  - 'prod'

dev_access_key_id: '<CHANGEME>'
dev_secret_access_key: '<CHANGEME>'

prod_access_key_id: '<CHANGEME>'
prod_secret_access_key: '<CHANGEME>'
 ```

| Variable | Description | Encrypted |
| ------ | ----------- | ----------- |
| `aws_credential_list: - "<CHANGEME>"` | AWS credential name list (`dev`, `prod` etc.) Must be alphanumeric |  |
| `<aws_environment>_access_key_id: <CHANGEME>` | AWS access key ID, prefixed with the target AWS environment | ✔ |
| `<aws_environment>_secret_access_key_id: <CHANGEME>` | AWS secret key ID, prefixed with the target AWS environment | ✔ |

## cluster.yml

Configuration variables required by the `provisioning_vars.yml.j2` file to provision of an Openshift cluster.

| Variable | Description | Encrypted |
| ------ | ----------- | ----------- |
| `cluster_credential_git_repo`  | SSH URL of the Github credential repository to be used |  |
| `cluster_pod_openshift_user`   | Openshift cluster pod username | ✔ |
| `cluster_pod_openshift_pass`   | Openshift cluster pod password | ✔ |
| `cluster_credential_bundle_aws_name` | AWS cluster credential bundle name |  |
| `cluster_type` | Cluster type. Should be set to 'dev' or 'poc' |
| `rh_user` | [Red Hat registry](https://docs.openshift.com/container-platform/3.11/install/configuring_inventory_file.html#advanced-install-configuring-registry-location) username | ✔ |
| `rh_pass` | [Red Hat registry](https://docs.openshift.com/container-platform/3.11/install/configuring_inventory_file.html#advanced-install-configuring-registry-location) password | ✔ |
| `dev_domain` | Domain name to be used for development (DEV) environments |  |
| `poc_domain` | Domain name to be used for Proof of Concept (POC) environments |  |
| `htpasswd_username` | Openshift cluster admin username |  |
| `htpasswd_password` | Openshift cluster admin password | ✔ |

## integreatly_vault.yml

Ansible Tower credentials values.

| Variable | Description | Encrypted |
| ------ | ----------- | ----------- |
| `tower_credential_bundle_vault_name` | The name of the tower credential bundle to be used  |
| `integreatly_vault` | The password associated with the tower credentials vault bundle name | ✔ |

## letsencrypt.yml

Private key to be used with Lets Encrypt.

| Variable | Description | Encrypted |
| ------ | ----------- | ----------- |
| `letsencrypt_private_key` | The user generated private key to be used with Lets Encrypt | ✔ |

## send_grid.yml

Send Grid credentials to be used to send a notification email if the Compare Project Variables job fails. Can be left blank if not required.

| Variable | Description | Encrypted |
| ------ | ----------- | ----------- |
| `send_grid_user` | The Send Grid user associated with the API key | ✔ |
| `send_grid_sender` | Sender email address | ✔ |
| `send_grid_password` | Password associated with the API key | ✔ |
| `send_grid_host` | Send Grid host |  |
| `send_grid_port` | Send Grid port number. Default is port 587 |  |
| `send_grid_email_recipients` | Email address of the intended recipients, comma separated if more than one recipient |  |

## tower_github_authentication.yml

Ansible [Social Auth](https://docs.ansible.com/ansible-tower/3.0.2/html/administration/social_auth.html) credentials.

| Variable | Description | Encrypted |
| ------ | ----------- | ----------- |
| `social_auth_github_org_name` | GitHub organizational name |  |
| `social_auth_github_org_key` | GitHub auth key | ✔ |
| `social_auth_github_org_secret` | GitHub auth secret | ✔ |
| `social_auth_github_org_organization_map` | GitHub auth organizational map |  |
| `social_auth_github_org_team_map` | [Team map](https://docs.ansible.com/ansible-tower/3.0.2/html/administration/social_auth.html#organization-and-team-mapping) variables used to map users to organizations |  |

## tower_github_scm.yml

Ansible Tower credential values.

| Variable | Description | Encrypted |
| ------ | ----------- | ----------- |
| `tower_github_scm_password` | The password to be used with the associated Github project | ✔ |
| `tower_github_scm` | The SSH key associated with the Github project | ✔ |

## tower_openshift_authentication.yml

Login credentials for the Target Openshift cluster.

| Variable | Description | Encrypted |
| ------ | ----------- | ----------- |
| `tower_openshift_username` | The username to be used to login to the Openshift cluster (requires admin permissions) | ✔ |
| `tower_openshift_password` | The password of the Openshift user specified | ✔ |
| `tower_openshift_master_url` | The hostname of the target Openshift cluster |  |

## tower_ssh.yml

Ansible Tower SSH configuration values.

| Variable | Description | Encrypted |
| ------ | ----------- | ----------- |
| `tower_ssh`  | The SSH key to be copied over to the Ansible tower instance | ✔ |
| `tower_ssh_become_password`  | sudo password for tower username associated with the tower credentials | ✔ |
| `tower_ssh_user` | The tower username associated with the tower credentials |  |

## tower_credentials

Credentials of the target Ansible Tower instances. Multiple tower instances can be supported. The name of each tower instance must be added to the `tower_instance_list`, and the associated credentials also specified with the tower instance name prefixed to each:

```bash
tower_instance_list:
  - 'dev'
  - 'prod'
  
dev_tower_host: '<CHANGEME>'
dev_tower_verify_ssl: False
dev_tower_username: '<CHANGEME>'
dev_tower_password: '<CHANGEME>'

prod_tower_host: '<CHANGEME>'
prod_tower_verify_ssl: True
prod_tower_username: '<CHANGEME>'
prod_tower_password: '<CHANGEME>'
 ```

| Variable | Description | Encrypted |
| ------ | ----------- | ----------- |
| `tower_instance_list: - "<CHANGEME>"` | List of target Tower instances (`dev`, `prod` etc.) Must be alphanumeric |  |
| `<tower_instance>_tower_host: <CHANGEME>` | The hostname of the Target Ansible Tower instance, prefixed with the target tower instance |  |
| `<tower_instance>_tower_verify_ssl: <CHANGEME>` | Whether SSL verification is required or not, prefixed with the target tower instance |  |
| `<tower_instance>_tower_username: <CHANGEME>` | The username of the Target Ansible Tower instance, prefixed with the target tower instance |  |
| `<tower_instance>_tower_password: <CHANGEME>` | The password of the Target Ansible Tower instance, prefixed with the target tower instance | ✔ |