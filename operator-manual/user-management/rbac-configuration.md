# RBAC Configuration

The RBAC feature enables restriction of access to AuthSafe resources. AuthSafe does not have its own user management system and provider . RBAC requires SSO Configuration. Once SSO are configured, additional RBAC roles can be defined, and SSO groups or local users can then be mapped to roles.

### Basic Built-in Roles[¶](https://argo-cd.readthedocs.io/en/stable/operator-manual/rbac/#basic-built-in-roles) <a href="#basic-built-in-roles" id="basic-built-in-roles"></a>

AuthSafe has two pre-defined roles (see below).

* `role:attachment-administrator`
* `role:attachment-viewer`
* `role:integration-administrator`
* `role:integration-viewer`
* `role:repository-administrator`
* `role:repository-viewer`
* `role:readonly` - read-only access to all resources
* `role:admin` - unrestricted access to all resources

These default built-in role definitions can be seen in [builtin-policy.csv](https://github.com/auth-safe/authsafe-server/blob/main/assets/builtin-policy.csv)

#### RBAC Permission Structure[¶](https://argo-cd.readthedocs.io/en/stable/operator-manual/rbac/#rbac-permission-structure) <a href="#rbac-permission-structure" id="rbac-permission-structure"></a>

Breaking down the permissions definition differs slightly between applications and every other resource type in AuthSafe.

*   All resources:

    `p, <role/user/group>, <resource>, <action>, <object>`

#### RBAC Resources and Actions. <a href="#rbac-resources-and-actions" id="rbac-resources-and-actions"></a>

\
