# Buildable Keycloak application stack for Kubernetes on Wodby

Deploy Keycloak with your own themes and providers on Kubernetes with Wodby:
your Git repository holds them, and Wodby builds Keycloak with them.

This repository defines the Wodby stack manifests and default service
composition for buildable Keycloak.

<!-- wodby:generated:start -->

## Stack contract

- [Keycloak stack on Wodby](https://wodby.com/stacks/keycloak)
- [Browse Wodby application stacks](https://wodby.com/stacks)
- [Keycloak stack guide](https://wodby.com/docs/2.0/stacks/catalog/keycloak/)
- [Wodby stack documentation](https://wodby.com/docs/2.0/stacks/)
- [Stack manifest reference](https://wodby.com/docs/2.0/stacks/template/)

## Service definitions

- [Buildable Keycloak service](https://github.com/wodby/service-keycloak-buildable)
- [PostgreSQL service](https://github.com/wodby/service-postgres)

## What's included

| Component / service | Default configuration |
| --- | --- |
| Keycloak<br>`keycloak` | required; enabled by default; links: `postgres` → `postgres` |
| PostgreSQL<br>`postgres` | required; enabled by default; volumes: `data` 20 GB |

Enabled optional services are selected by default but can be excluded when an
app is created. Disabled optional services are available but not selected by
default. Required services cannot be excluded.

## Validate the stack manifest

```bash
wodby stack validate-manifest stack.yml --org <org-id>
```

<!-- wodby:generated:end -->

## Deploy this stack

Connect a Git repository started from the
[Keycloak boilerplate](https://github.com/wodby/keycloak-boilerplate):

- `themes/` holds your login, account, email or admin themes.
- `providers/` holds your provider jars.

Choose the Keycloak version when you create the app. The build starts from the
official Keycloak image of that version, adds your themes and providers and
runs Keycloak's build, so Keycloak starts without rebuilding. Select your theme
for a realm under **Realm settings > Themes**. To run Keycloak without your own
themes or providers, use the [Keycloak stack](https://github.com/wodby/stack-keycloak).

## Maintain a custom version

1. Fork this repository.
2. Edit the stack manifest.
3. Import the repository as a [Git-backed stack](https://wodby.com/docs/2.0/stacks/create/#create-a-git-backed-stack).

When replacing or renaming a stack service, update every related link target
and derivative reference. Stack-local names and referenced service names are
distinct identifiers.
