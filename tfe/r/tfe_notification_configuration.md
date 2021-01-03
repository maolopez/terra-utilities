# tfe_notification_configuration

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
module "tfe_notification_configuration" {
  source = "./modules/tfe/r/tfe_notification_configuration"

  # destination_type - (required) is a type of string
  destination_type = null
  # email_addresses - (optional) is a type of set of string
  email_addresses = []
  # email_user_ids - (optional) is a type of set of string
  email_user_ids = []
  # enabled - (optional) is a type of bool
  enabled = null
  # name - (required) is a type of string
  name = null
  # token - (optional) is a type of string
  token = null
  # triggers - (optional) is a type of set of string
  triggers = []
  # url - (optional) is a type of string
  url = null
  # workspace_external_id - (optional) is a type of string
  workspace_external_id = null
  # workspace_id - (optional) is a type of string
  workspace_id = null
}
```

[top](#index)

### Variables

```terraform
variable "destination_type" {
  description = "(required)"
  type        = string
}

variable "email_addresses" {
  description = "(optional)"
  type        = set(string)
  default     = null
}

variable "email_user_ids" {
  description = "(optional)"
  type        = set(string)
  default     = null
}

variable "enabled" {
  description = "(optional)"
  type        = bool
  default     = null
}

variable "name" {
  description = "(required)"
  type        = string
}

variable "token" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "triggers" {
  description = "(optional)"
  type        = set(string)
  default     = null
}

variable "url" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "workspace_external_id" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "workspace_id" {
  description = "(optional)"
  type        = string
  default     = null
}
```

[top](#index)

### Resource

```terraform
resource "tfe_notification_configuration" "this" {
  destination_type      = var.destination_type
  email_addresses       = var.email_addresses
  email_user_ids        = var.email_user_ids
  enabled               = var.enabled
  name                  = var.name
  token                 = var.token
  triggers              = var.triggers
  url                   = var.url
  workspace_external_id = var.workspace_external_id
  workspace_id          = var.workspace_id
}
```

[top](#index)

### Outputs

```terraform
output "email_addresses" {
  description = "returns a set of string"
  value       = tfe_notification_configuration.this.email_addresses
}

output "email_user_ids" {
  description = "returns a set of string"
  value       = tfe_notification_configuration.this.email_user_ids
}

output "id" {
  description = "returns a string"
  value       = tfe_notification_configuration.this.id
}

output "workspace_external_id" {
  description = "returns a string"
  value       = tfe_notification_configuration.this.workspace_external_id
}

output "workspace_id" {
  description = "returns a string"
  value       = tfe_notification_configuration.this.workspace_id
}

output "this" {
  value = tfe_notification_configuration.this
}
```

[top](#index)