# okta_group_rule

[back](../okta.md)

### Index

- [Example Usage](#example-usage)
- [Variables](#variables)
- [Resource](#resource)
- [Outputs](#outputs)

### Terraform

```terraform
terraform {
  required_providers {
    okta = ">= 3.7.4"
  }
}
```

[top](#index)

### Example Usage

```terraform
module "okta_group_rule" {
  source = "./modules/okta/r/okta_group_rule"

  # expression_type - (optional) is a type of string
  expression_type = null
  # expression_value - (required) is a type of string
  expression_value = null
  # group_assignments - (required) is a type of set of string
  group_assignments = []
  # name - (required) is a type of string
  name = null
  # status - (optional) is a type of string
  status = null
}
```

[top](#index)

### Variables

```terraform
variable "expression_type" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "expression_value" {
  description = "(required)"
  type        = string
}

variable "group_assignments" {
  description = "(required)"
  type        = set(string)
}

variable "name" {
  description = "(required)"
  type        = string
}

variable "status" {
  description = "(optional)"
  type        = string
  default     = null
}
```

[top](#index)

### Resource

```terraform
resource "okta_group_rule" "this" {
  expression_type   = var.expression_type
  expression_value  = var.expression_value
  group_assignments = var.group_assignments
  name              = var.name
  status            = var.status
}
```

[top](#index)

### Outputs

```terraform
output "id" {
  description = "returns a string"
  value       = okta_group_rule.this.id
}

output "this" {
  value = okta_group_rule.this
}
```

[top](#index)