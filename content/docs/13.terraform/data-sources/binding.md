---
# generated by https://github.com/hashicorp/terraform-plugin-docs
title: kestra_binding
editLink: false
description: |-
  Use this data source to access information about an existing Kestra binding
---

# kestra_binding (Data Source)

Use this data source to access information about an existing Kestra binding

## Example Usage

```hcl
data "kestra_binding" "example" {
  binding_id = "65DsawPfiJPkTkZJIPX6jQ"
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `binding_id` (String) The binding id.

### Read-Only

- `external_id` (String) The binding external id.
- `id` (String) The ID of this resource.
- `namespace` (String) The linked namespace.
- `role_id` (String) The role id.
- `tenant_id` (String) The tenant id.
- `type` (String) The binding type.
