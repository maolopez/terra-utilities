# fortios_dlp_sensor

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
module "fortios_dlp_sensor" {
  source = "./modules/fortios/r/fortios_dlp_sensor"

  # comment - (optional) is a type of string
  comment = null
  # dlp_log - (optional) is a type of string
  dlp_log = null
  # extended_log - (optional) is a type of string
  extended_log = null
  # flow_based - (optional) is a type of string
  flow_based = null
  # full_archive_proto - (optional) is a type of string
  full_archive_proto = null
  # nac_quar_log - (optional) is a type of string
  nac_quar_log = null
  # name - (required) is a type of string
  name = null
  # options - (optional) is a type of string
  options = null
  # replacemsg_group - (optional) is a type of string
  replacemsg_group = null
  # summary_proto - (optional) is a type of string
  summary_proto = null

  filter = [{
    action             = null
    archive            = null
    company_identifier = null
    expiry             = null
    file_size          = null
    file_type          = null
    filter_by          = null
    fp_sensitivity = [{
      name = null
    }]
    id               = null
    match_percentage = null
    name             = null
    proto            = null
    regexp           = null
    severity         = null
    type             = null
  }]
}
```

[top](#index)

### Variables

```terraform
variable "comment" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "dlp_log" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "extended_log" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "flow_based" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "full_archive_proto" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "nac_quar_log" {
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

variable "replacemsg_group" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "summary_proto" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "filter" {
  description = "nested block: NestingList, min items: 0, max items: 0"
  type = set(object(
    {
      action             = string
      archive            = string
      company_identifier = string
      expiry             = string
      file_size          = number
      file_type          = number
      filter_by          = string
      fp_sensitivity = list(object(
        {
          name = string
        }
      ))
      id               = number
      match_percentage = number
      name             = string
      proto            = string
      regexp           = string
      severity         = string
      type             = string
    }
  ))
  default = []
}
```

[top](#index)

### Resource

```terraform
resource "fortios_dlp_sensor" "this" {
  comment            = var.comment
  dlp_log            = var.dlp_log
  extended_log       = var.extended_log
  flow_based         = var.flow_based
  full_archive_proto = var.full_archive_proto
  nac_quar_log       = var.nac_quar_log
  name               = var.name
  options            = var.options
  replacemsg_group   = var.replacemsg_group
  summary_proto      = var.summary_proto

  dynamic "filter" {
    for_each = var.filter
    content {
      action             = filter.value["action"]
      archive            = filter.value["archive"]
      company_identifier = filter.value["company_identifier"]
      expiry             = filter.value["expiry"]
      file_size          = filter.value["file_size"]
      file_type          = filter.value["file_type"]
      filter_by          = filter.value["filter_by"]
      id                 = filter.value["id"]
      match_percentage   = filter.value["match_percentage"]
      name               = filter.value["name"]
      proto              = filter.value["proto"]
      regexp             = filter.value["regexp"]
      severity           = filter.value["severity"]
      type               = filter.value["type"]

      dynamic "fp_sensitivity" {
        for_each = filter.value.fp_sensitivity
        content {
          name = fp_sensitivity.value["name"]
        }
      }

    }
  }

}
```

[top](#index)

### Outputs

```terraform
output "dlp_log" {
  description = "returns a string"
  value       = fortios_dlp_sensor.this.dlp_log
}

output "extended_log" {
  description = "returns a string"
  value       = fortios_dlp_sensor.this.extended_log
}

output "flow_based" {
  description = "returns a string"
  value       = fortios_dlp_sensor.this.flow_based
}

output "full_archive_proto" {
  description = "returns a string"
  value       = fortios_dlp_sensor.this.full_archive_proto
}

output "id" {
  description = "returns a string"
  value       = fortios_dlp_sensor.this.id
}

output "nac_quar_log" {
  description = "returns a string"
  value       = fortios_dlp_sensor.this.nac_quar_log
}

output "options" {
  description = "returns a string"
  value       = fortios_dlp_sensor.this.options
}

output "replacemsg_group" {
  description = "returns a string"
  value       = fortios_dlp_sensor.this.replacemsg_group
}

output "summary_proto" {
  description = "returns a string"
  value       = fortios_dlp_sensor.this.summary_proto
}

output "this" {
  value = fortios_dlp_sensor.this
}
```

[top](#index)