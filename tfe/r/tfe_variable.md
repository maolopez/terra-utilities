# tfe_variable

[back](../tfe.md)

### Index

- [Example Usage](#example-usage)
- [Variables](#variables)
- [Resource](#resource)
- [Outputs](#outputs)

### Terraform

```terraform
terraform {
  required_providers {
    tfe = ">= 0.23.0"
  }
}
```

[top](#index)

### Example Usage

```terraform
module "tfe_variable" {
  source = "./modules/tfe/r/tfe_variable"

  # category - (required) is a type of string
  category = null
  # description - (optional) is a type of string
  description = null
  # hcl - (optional) is a type of bool
  hcl = null
  # key - (required) is a type of string
  key = null
  # sensitive - (optional) is a type of bool
  sensitive = null
  # value - (optional) is a type of string
  value = null
  # workspace_id - (required) is a type of string
  workspace_id = null
}
```

[top](#index)

### Variables

```terraform
variable "category" {
  description = "(required)"
  type        = string
}

variable "description" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "hcl" {
  description = "(optional)"
  type        = bool
  default     = null
}

variable "key" {
  description = "(required)"
  type        = string
}

variable "sensitive" {
  description = "(optional)"
  type        = bool
  default     = null
}

variable "value" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "workspace_id" {
  description = "(required)"
  type        = string
}
```

[top](#index)

### Resource

```terraform
resource "tfe_variable" "this" {
  category     = var.category
  description  = var.description
  hcl          = var.hcl
  key          = var.key
  sensitive    = var.sensitive
  value        = var.value
  workspace_id = var.workspace_id
}
```

[top](#index)

### Outputs

```terraform
output "id" {
  description = "returns a string"
  value       = tfe_variable.this.id
}

output "this" {
  value = tfe_variable.this
}
```

[top](#index)