# oci_database_vm_cluster_patch_history_entries

[back](../oci.md)

### Index

- [Example Usage](#example-usage)
- [Variables](#variables)
- [Datasource](#datasource)
- [Outputs](#outputs)

### Terraform

```terraform
terraform {
  required_providers {
    oci = ">= 4.7.0"
  }
}
```

[top](#index)

### Example Usage

```terraform
module "oci_database_vm_cluster_patch_history_entries" {
  source = "./modules/oci/d/oci_database_vm_cluster_patch_history_entries"

  # vm_cluster_id - (required) is a type of string
  vm_cluster_id = null

  filter = [{
    name   = null
    regex  = null
    values = []
  }]
}
```

[top](#index)

### Variables

```terraform
variable "vm_cluster_id" {
  description = "(required)"
  type        = string
}

variable "filter" {
  description = "nested block: NestingSet, min items: 0, max items: 0"
  type = set(object(
    {
      name   = string
      regex  = bool
      values = list(string)
    }
  ))
  default = []
}
```

[top](#index)

### Datasource

```terraform
data "oci_database_vm_cluster_patch_history_entries" "this" {
  vm_cluster_id = var.vm_cluster_id

  dynamic "filter" {
    for_each = var.filter
    content {
      name   = filter.value["name"]
      regex  = filter.value["regex"]
      values = filter.value["values"]
    }
  }

}
```

[top](#index)

### Outputs

```terraform
output "id" {
  description = "returns a string"
  value       = data.oci_database_vm_cluster_patch_history_entries.this.id
}

output "patch_history_entries" {
  description = "returns a list of object"
  value       = data.oci_database_vm_cluster_patch_history_entries.this.patch_history_entries
}

output "this" {
  value = oci_database_vm_cluster_patch_history_entries.this
}
```

[top](#index)