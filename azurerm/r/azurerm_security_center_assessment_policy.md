# azurerm_security_center_assessment_policy

[back](../azurerm.md)

### Index

- [Example Usage](#example-usage)
- [Variables](#variables)
- [Resource](#resource)
- [Outputs](#outputs)

### Terraform

```terraform
terraform {
  required_providers {
    azurerm = ">= 2.53.0"
  }
}
```

[top](#index)

### Example Usage

```terraform
module "azurerm_security_center_assessment_policy" {
  source = "./modules/azurerm/r/azurerm_security_center_assessment_policy"

  # description - (required) is a type of string
  description = null
  # display_name - (required) is a type of string
  display_name = null
  # implementation_effort - (optional) is a type of string
  implementation_effort = null
  # remediation_description - (optional) is a type of string
  remediation_description = null
  # severity - (optional) is a type of string
  severity = null
  # threats - (optional) is a type of set of string
  threats = []
  # user_impact - (optional) is a type of string
  user_impact = null

  timeouts = [{
    create = null
    delete = null
    read   = null
    update = null
  }]
}
```

[top](#index)

### Variables

```terraform
variable "description" {
  description = "(required)"
  type        = string
}

variable "display_name" {
  description = "(required)"
  type        = string
}

variable "implementation_effort" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "remediation_description" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "severity" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "threats" {
  description = "(optional)"
  type        = set(string)
  default     = null
}

variable "user_impact" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "timeouts" {
  description = "nested block: NestingSingle, min items: 0, max items: 0"
  type = set(object(
    {
      create = string
      delete = string
      read   = string
      update = string
    }
  ))
  default = []
}
```

[top](#index)

### Resource

```terraform
resource "azurerm_security_center_assessment_policy" "this" {
  description             = var.description
  display_name            = var.display_name
  implementation_effort   = var.implementation_effort
  remediation_description = var.remediation_description
  severity                = var.severity
  threats                 = var.threats
  user_impact             = var.user_impact

  dynamic "timeouts" {
    for_each = var.timeouts
    content {
      create = timeouts.value["create"]
      delete = timeouts.value["delete"]
      read   = timeouts.value["read"]
      update = timeouts.value["update"]
    }
  }

}
```

[top](#index)

### Outputs

```terraform
output "id" {
  description = "returns a string"
  value       = azurerm_security_center_assessment_policy.this.id
}

output "name" {
  description = "returns a string"
  value       = azurerm_security_center_assessment_policy.this.name
}

output "this" {
  value = azurerm_security_center_assessment_policy.this
}
```

[top](#index)