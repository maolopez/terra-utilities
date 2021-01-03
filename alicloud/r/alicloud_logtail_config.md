# alicloud_logtail_config

[back](../alicloud.md)

### Index

- [Example Usage](#example-usage)
- [Variables](#variables)
- [Resource](#resource)
- [Outputs](#outputs)

### Terraform

```terraform
terraform {
  required_providers {
    alicloud = ">= 1.111.0"
  }
}
```

[top](#index)

### Example Usage

```terraform
module "alicloud_logtail_config" {
  source = "./modules/alicloud/r/alicloud_logtail_config"

  # input_detail - (required) is a type of string
  input_detail = null
  # input_type - (required) is a type of string
  input_type = null
  # log_sample - (optional) is a type of string
  log_sample = null
  # logstore - (required) is a type of string
  logstore = null
  # name - (required) is a type of string
  name = null
  # output_type - (required) is a type of string
  output_type = null
  # project - (required) is a type of string
  project = null
}
```

[top](#index)

### Variables

```terraform
variable "input_detail" {
  description = "(required)"
  type        = string
}

variable "input_type" {
  description = "(required)"
  type        = string
}

variable "log_sample" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "logstore" {
  description = "(required)"
  type        = string
}

variable "name" {
  description = "(required)"
  type        = string
}

variable "output_type" {
  description = "(required)"
  type        = string
}

variable "project" {
  description = "(required)"
  type        = string
}
```

[top](#index)

### Resource

```terraform
resource "alicloud_logtail_config" "this" {
  input_detail = var.input_detail
  input_type   = var.input_type
  log_sample   = var.log_sample
  logstore     = var.logstore
  name         = var.name
  output_type  = var.output_type
  project      = var.project
}
```

[top](#index)

### Outputs

```terraform
output "id" {
  description = "returns a string"
  value       = alicloud_logtail_config.this.id
}

output "this" {
  value = alicloud_logtail_config.this
}
```

[top](#index)