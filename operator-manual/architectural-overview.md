# 🛴 Architectural Overview

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

* Server: is a connect-RPC server, which exposes API consumed by Web. It has the following responsibilities:
  * ticket management and status reporting.
  * repository and artifact credential management.
  * delegate authentication to external identity providers.
  * RBAC enforcement.
* Workflow server: temporal, manage task and state of workflows, response to rpc call from worker with workflow task.
* Worker: advancing workflow with workflow task it get from server, response task completed/failed upon task execution result.  It has the following responsibilities:
  * Execute workflow tasks, which including:
    * evaluate list of approvers.
    * send notification to approvers.
    * record approver submission and evalute result.
    * grant and revoke permission.
