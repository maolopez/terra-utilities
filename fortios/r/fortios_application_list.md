# fortios_application_list

[back](../fortios.md)

### Index

- [Example Usage](#example-usage)
- [Variables](#variables)
- [Resource](#resource)
- [Outputs](#outputs)

### Terraform

```terraform
terraform {
  required_providers {
    fortios = ">= 1.6.18"
  }
}
```

[top](#index)

### Example Usage

```terraform
module "fortios_application_list" {
  source = "./modules/fortios/r/fortios_application_list"

  # app_replacemsg - (optional) is a type of string
  app_replacemsg = null
  # comment - (optional) is a type of string
  comment = null
  # deep_app_inspection - (optional) is a type of string
  deep_app_inspection = null
  # enforce_default_app_port - (optional) is a type of string
  enforce_default_app_port = null
  # extended_log - (optional) is a type of string
  extended_log = null
  # name - (required) is a type of string
  name = null
  # options - (optional) is a type of string
  options = null
  # other_application_action - (optional) is a type of string
  other_application_action = null
  # other_application_log - (optional) is a type of string
  other_application_log = null
  # p2p_black_list - (optional) is a type of string
  p2p_black_list = null
  # replacemsg_group - (optional) is a type of string
  replacemsg_group = null
  # unknown_application_action - (optional) is a type of string
  unknown_application_action = null
  # unknown_application_log - (optional) is a type of string
  unknown_application_log = null

  entries = [{
    action = null
    application = [{
      id = null
    }]
    behavior = null
    category = [{
      id = null
    }]
    id         = null
    log        = null
    log_packet = null
    parameters = [{
      id    = null
      value = null
    }]
    per_ip_shaper     = null
    popularity        = null
    protocols         = null
    quarantine        = null
    quarantine_expiry = null
    quarantine_log    = null
    rate_count        = null
    rate_duration     = null
    rate_mode         = null
    rate_track        = null
    risk = [{
      level = null
    }]
    session_ttl    = null
    shaper         = null
    shaper_reverse = null
    sub_category = [{
      id = null
    }]
    technology = null
    vendor     = null
  }]
}
```

[top](#index)

### Variables

```terraform
variable "app_replacemsg" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "comment" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "deep_app_inspection" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "enforce_default_app_port" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "extended_log" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "name" {
  description = "(required)"
  type        = string
}

variable "options" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "other_application_action" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "other_application_log" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "p2p_black_list" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "replacemsg_group" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "unknown_application_action" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "unknown_application_log" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "entries" {
  description = "nested block: NestingList, min items: 0, max items: 0"
  type = set(object(
    {
      action = string
      application = list(object(
        {
          id = number
        }
      ))
      behavior = string
      category = list(object(
        {
          id = number
        }
      ))
      id         = number
      log        = string
      log_packet = string
      parameters = list(object(
        {
          id    = number
          value = string
        }
      ))
      per_ip_shaper     = string
      popularity        = string
      protocols         = string
      quarantine        = string
      quarantine_expiry = string
      quarantine_log    = string
      rate_count        = number
      rate_duration     = number
      rate_mode         = string
      rate_track        = string
      risk = list(object(
        {
          level = number
        }
      ))
      session_ttl    = number
      shaper         = string
      shaper_reverse = string
      sub_category = list(object(
        {
          id = number
        }
      ))
      technology = string
      vendor     = string
    }
  ))
  default = []
}
```

[top](#index)

### Resource

```terraform
resource "fortios_application_list" "this" {
  app_replacemsg             = var.app_replacemsg
  comment                    = var.comment
  deep_app_inspection        = var.deep_app_inspection
  enforce_default_app_port   = var.enforce_default_app_port
  extended_log               = var.extended_log
  name                       = var.name
  options                    = var.options
  other_application_action   = var.other_application_action
  other_application_log      = var.other_application_log
  p2p_black_list             = var.p2p_black_list
  replacemsg_group           = var.replacemsg_group
  unknown_application_action = var.unknown_application_action
  unknown_application_log    = var.unknown_application_log

  dynamic "entries" {
    for_each = var.entries
    content {
      action            = entries.value["action"]
      behavior          = entries.value["behavior"]
      id                = entries.value["id"]
      log               = entries.value["log"]
      log_packet        = entries.value["log_packet"]
      per_ip_shaper     = entries.value["per_ip_shaper"]
      popularity        = entries.value["popularity"]
      protocols         = entries.value["protocols"]
      quarantine        = entries.value["quarantine"]
      quarantine_expiry = entries.value["quarantine_expiry"]
      quarantine_log    = entries.value["quarantine_log"]
      rate_count        = entries.value["rate_count"]
      rate_duration     = entries.value["rate_duration"]
      rate_mode         = entries.value["rate_mode"]
      rate_track        = entries.value["rate_track"]
      session_ttl       = entries.value["session_ttl"]
      shaper            = entries.value["shaper"]
      shaper_reverse    = entries.value["shaper_reverse"]
      technology        = entries.value["technology"]
      vendor            = entries.value["vendor"]

      dynamic "application" {
        for_each = entries.value.application
        content {
          id = application.value["id"]
        }
      }

      dynamic "category" {
        for_each = entries.value.category
        content {
          id = category.value["id"]
        }
      }

      dynamic "parameters" {
        for_each = entries.value.parameters
        content {
          id    = parameters.value["id"]
          value = parameters.value["value"]
        }
      }

      dynamic "risk" {
        for_each = entries.value.risk
        content {
          level = risk.value["level"]
        }
      }

      dynamic "sub_category" {
        for_each = entries.value.sub_category
        content {
          id = sub_category.value["id"]
        }
      }

    }
  }

}
```

[top](#index)

### Outputs

```terraform
output "app_replacemsg" {
  description = "returns a string"
  value       = fortios_application_list.this.app_replacemsg
}

output "deep_app_inspection" {
  description = "returns a string"
  value       = fortios_application_list.this.deep_app_inspection
}

output "enforce_default_app_port" {
  description = "returns a string"
  value       = fortios_application_list.this.enforce_default_app_port
}

output "extended_log" {
  description = "returns a string"
  value       = fortios_application_list.this.extended_log
}

output "id" {
  description = "returns a string"
  value       = fortios_application_list.this.id
}

output "options" {
  description = "returns a string"
  value       = fortios_application_list.this.options
}

output "other_application_action" {
  description = "returns a string"
  value       = fortios_application_list.this.other_application_action
}

output "other_application_log" {
  description = "returns a string"
  value       = fortios_application_list.this.other_application_log
}

output "p2p_black_list" {
  description = "returns a string"
  value       = fortios_application_list.this.p2p_black_list
}

output "replacemsg_group" {
  description = "returns a string"
  value       = fortios_application_list.this.replacemsg_group
}

output "unknown_application_action" {
  description = "returns a string"
  value       = fortios_application_list.this.unknown_application_action
}

output "unknown_application_log" {
  description = "returns a string"
  value       = fortios_application_list.this.unknown_application_log
}

output "this" {
  value = fortios_application_list.this
}
```

[top](#index)