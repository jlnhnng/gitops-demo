## Before you deploy, fill in these placeholders and create the secret:

- chart `version` is pinned to 9.4.1; bump it deliberately
- `ingress.className`
- the Files and Volumes StorageClass names
- `nextcloud.host` / `trustedDomains`

### Create the secret as a Project Secret
Use a Project Secret, not a file in Git. NKP federates it to the project's clusters.

> UI: Project → Secrets → Create, name `nextcloud-secrets`, with these keys:
``` txt
| key | value |
|---|---|
| nextcloud-username | admin |
| nextcloud-password | <strong> |
| db-username | nextcloud |
| db-password | <strong> |
| db-admin-password | <strong> |
| redis-password | <strong> |
```