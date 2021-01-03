# oci_core_remote_peering_connections

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
module "oci_core_remote_peering_connections" {
  source = "./modules/oci/d/oci_core_remote_peering_connections"

  # compartment_id - (required) is a type of string
  compartment_id = null
  # drg_id - (optional) is a type of string
  drg_id = null

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
variable "compartment_id" {
  description = "(required)"
  type        = string
}

variable "drg_id" {
  description = "(optional)"
  type        = string
  default     = null
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
data "oci_core_remote_peering_connections" "this" {
  compartment_id = var.compartment_id
  drg_id         = var.drg_id

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
  value       = data.oci_core_remote_peering_connections.this.id
}

output "remote_peering_connections" {
  description = "returns a list of object"
  value       = data.oci_core_remote_peering_connections.this.remote_peering_connections
}

output "this" {
  value = oci_core_remote_peering_connections.this
}
```

[top](#index)