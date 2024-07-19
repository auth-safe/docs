---
description: >-
  Let's assume you're familiar with core Git, Terraform and Rule Engine concepts
  . Below are some of the concepts that are specific to Authsafe.
---

# 💡 Core concepts

Let's assume you're familiar with core Git, Terraform and Rule Engine concepts . Below are some of the concepts that are specific to Authsafe.

<details>

<summary><strong>Attachment</strong></summary>

Attachment attach an integration with its corresponding terraform module.

Integration contains required authentication details of how to access the requested target.

Terraform module contains instruction to create/grant credential in the requested target.

</details>

<details>

<summary><strong>Integration</strong></summary>

Integration is an intermediate between authsafe and secret backend that support key-value secret store.

Supported backend:

* Hashicorp Vault
* AWS Secret Manager

</details>

<details>

<summary><strong>Rule</strong></summary>

Rule is evaluated per request.

A rule evaluation request contains ticket and attachment data. Rule evaluation request will be evaluated against a list of rule stored in a git repository.

Sample rule: [https://github.com/auth-safe/example-rule](https://github.com/auth-safe/example-rule)

Syntax: [https://docs.drools.org/8.39.0.Final/drools-docs/docs-website/drools/language-reference/index.html#:\~:text=Drools%20Rule%20Language%20(DRL)%20is,drl%20text%20files.](https://docs.drools.org/8.39.0.Final/drools-docs/docs-website/drools/language-reference/index.html)&#x20;

</details>

<details>

<summary><strong>Repository</strong></summary>



Repository store terraform module that will be applied to grant permission to an user. Two important aspects:

*   Variable

    Authsafe expect administrator to provide serveral variable with exact names:

    * user\_email: this will be extracted from user's Authorization token
*   Output

    Authsafe will save this output for user to download it later. Example use case is: terraform module that create user in MySQL database, user request SSH key to access Virtual Machine,...

</details>







