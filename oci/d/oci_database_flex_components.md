# oci_database_flex_components

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
module "oci_database_flex_components" {
  source = "./modules/oci/d/oci_database_flex_components"

  # compartment_id - (required) is a type of string
  compartment_id = null
  # name - (optional) is a type of string
  name = null

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

variable "name" {
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
data "oci_database_flex_components" "this" {
  compartment_id = var.compartment_id
  name           = var.name

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
output "flex_component_collection" {
  description = "returns a list of object"
  value       = data.oci_database_flex_components.this.flex_component_collection
}

output "id" {
  description = "returns a string"
  value       = data.oci_database_flex_components.this.id
}

output "this" {
  value = oci_database_flex_components.this
}
```

[top](#index)