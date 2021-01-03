# oci_autoscaling_auto_scaling_configurations

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
module "oci_autoscaling_auto_scaling_configurations" {
  source = "./modules/oci/d/oci_autoscaling_auto_scaling_configurations"

  # compartment_id - (required) is a type of string
  compartment_id = null
  # display_name - (optional) is a type of string
  display_name = null

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

variable "display_name" {
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
data "oci_autoscaling_auto_scaling_configurations" "this" {
  compartment_id = var.compartment_id
  display_name   = var.display_name

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
output "auto_scaling_configurations" {
  description = "returns a list of object"
  value       = data.oci_autoscaling_auto_scaling_configurations.this.auto_scaling_configurations
}

output "id" {
  description = "returns a string"
  value       = data.oci_autoscaling_auto_scaling_configurations.this.id
}

output "this" {
  value = oci_autoscaling_auto_scaling_configurations.this
}
```

[top](#index)