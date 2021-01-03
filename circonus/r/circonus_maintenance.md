# circonus_maintenance

[back](../circonus.md)

### Index

- [Example Usage](#example-usage)
- [Variables](#variables)
- [Resource](#resource)
- [Outputs](#outputs)

### Terraform

```terraform
terraform {
  required_providers {
    circonus = ">= 0.11.4"
  }
}
```

[top](#index)

### Example Usage

```terraform
module "circonus_maintenance" {
  source = "./modules/circonus/r/circonus_maintenance"

  # account - (optional) is a type of string
  account = null
  # check - (optional) is a type of string
  check = null
  # notes - (optional) is a type of string
  notes = null
  # rule_set - (optional) is a type of string
  rule_set = null
  # severities - (required) is a type of list of string
  severities = []
  # start - (required) is a type of string
  start = null
  # stop - (required) is a type of string
  stop = null
  # tags - (optional) is a type of list of string
  tags = []
  # target - (optional) is a type of string
  target = null
}
```

[top](#index)

### Variables

```terraform
variable "account" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "check" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "notes" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "rule_set" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "severities" {
  description = "(required)"
  type        = list(string)
}

variable "start" {
  description = "(required)"
  type        = string
}

variable "stop" {
  description = "(required)"
  type        = string
}

variable "tags" {
  description = "(optional)"
  type        = list(string)
  default     = null
}

variable "target" {
  description = "(optional)"
  type        = string
  default     = null
}
```

[top](#index)

### Resource

```terraform
resource "circonus_maintenance" "this" {
  account    = var.account
  check      = var.check
  notes      = var.notes
  rule_set   = var.rule_set
  severities = var.severities
  start      = var.start
  stop       = var.stop
  tags       = var.tags
  target     = var.target
}
```

[top](#index)

### Outputs

```terraform
output "id" {
  description = "returns a string"
  value       = circonus_maintenance.this.id
}

output "this" {
  value = circonus_maintenance.this
}
```

[top](#index)