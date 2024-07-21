# 🪝 Writing rule

AuthSafe rule has format of:

```
When
   <Condition is true>
Then
   <Take desired Action>
```

The most important part of a Rule is its when part. If the **when** part is satisfied, the **then** part is triggered.

```
rule  <rule_name> <rule_description>
   <attribute> <value> {
   when
      <conditions>

   then
      <actions>
}
```

There are 3 variables that will be supplied with each rule evaluation request: ticket, attachment, result.

Available attributes:

<details>

<summary>ticket</summary>

* `ID: string`

<!---->

* `CreatedAt: time`

<!---->

* `UpdatedAt: time`

<!---->

* `Description: string`

<!---->

* `Owner: string`

<!---->

* `StartTime: time`

<!---->

* `EndTime: time`

<!---->

* `Status: string`

<!---->

* `AttachmentID: number`

</details>

<details>

<summary>attachment</summary>

* `Short: string`
* `Long: string`
* `RepositoryID: number`
* `Path: string`
* `Revision: string`
* `IntegrationID: number`

</details>

<details>

<summary>result</summary>

* `MaxDurationHour: string`
* `Approvers: string`
* `SendNotificationTo: []string`
* `MinimumApproval: number`
* `AdditionalRequiredApprovers: []string`

</details>

Available methods:

<details>

<summary>ticket</summary>

* `CanUpdate(): bool`

<!---->

* `ValidTime(): bool`

<!---->

* `Ongoing(): bool`

</details>

<details>

<summary>attachment</summary>

* `GetOwners(): []string`
* `ContainsOwner(email: string): bool`

</details>

<details>

<summary>result</summary>

* `AppendApprovers(emails: []string)`

<!---->

* `AppendAdditionalRequiredApprovers(emails: []string)`

<!---->

* `AppendNotificationSubscriber(emails: []string)`

</details>

You can invoke any of the above attribute/method in rule. For example, a rule to by-pass approval cycle for attachment owner is:

```
rule OwnerByPass "OwnerByPass" salience 0 {
    when
        attachment.ContainsOwner(ticket.Owner)
    then
        result.MinimumApproval=0;
        Changed("result.MinimumApproval");
        Retract("OwnerByPass");
        Complete();
}
```

By default, all Rules are assigned a salience of `0`.

Because all nonspecified Rules are salience 0, it's easy for the engine to pick which Rule to execute when there are multiple Rules matches the `when` condition. If there are multiple Rules with matching priorities, the engine will choose the first one found.

Salience for Rule can be a value below zero (reaching into the negative) to ensure a Rule has even lower priority than the default. This will ensure that a Rule's action will be executed last, after all other Rules are evaluated.

***

**Make sure to push your rule to Git so AuthSafe can discover it.**
