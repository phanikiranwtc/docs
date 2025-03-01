---
# generated by https://github.com/hashicorp/terraform-plugin-docs
title: kestra_user
editLink: false
description: |-
  Use this data source to access information about an existing Kestra User.
---

# kestra_user (Data Source)

Use this data source to access information about an existing Kestra User.

## Example Usage

```hcl
data "kestra_user" "example" {
  user_id = "68xAawPfiJPkTkZJIPX6jQ"
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `user_id` (String) The user.

### Optional

- `namespace` (String) The linked namespace.

### Read-Only

- `description` (String) The user description.
- `email` (String) The user email.
- `first_name` (String) The user first name.
- `groups` (List of String) The user global roles in yaml string.
- `id` (String) The ID of this resource.
- `last_name` (String) The user last name.
- `username` (String) The user name.
