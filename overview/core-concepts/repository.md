---
description: >-
  Repository store terraform module that will be applied to grant permission to
  an user. Two important aspects:
---

# Repository

*   Variable

    Authsafe expect administrator to provide serveral variable with exact names:

    * user\_email: this will be extracted from user's Authorization token
*   Output

    Authsafe will save this output for user to download it later. Example use case is: terraform module that create user in MySQL database, user request SSH key to access Virtual Machine,...
