# ✨ Getting started

{% hint style="info" %}
**Tip:** This guide assumes you have a grounding in the tools that AuthSafe is based on. Please read Understand the basics to learn about these tools.
{% endhint %}

## Try out authsafe

### How to run

* Install [docker-compose](https://docs.docker.com/compose/install/)
* Install [go](https://go.dev/doc/install)
* Install [terraform](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli)
* Verify docker-compose

```bash
docker-compose -v
```

* Verify go

```bash
go version
```

* Verify terraform

```bash
terraform version
```

* Update hostfile:

```
sudo vi /etc/hosts
...
127.0.0.1 keycloak
127.0.0.1 redis
127.0.0.1 vault
127.0.0.1 mailhog
127.0.0.1 temporal
127.0.0.1 mysql
```

* Install AuthSafe

```
brew install authsafe
```

* Run testdrive

```
authsafe testdrive
```
