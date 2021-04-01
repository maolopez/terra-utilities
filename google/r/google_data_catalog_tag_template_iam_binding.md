# google_data_catalog_tag_template_iam_binding

[back](../google.md)

### Index

- [Example Usage](#example-usage)
- [Variables](#variables)
- [Resource](#resource)
- [Outputs](#outputs)

### Terraform

```terraform
terraform {
  required_providers {
    google = ">= 3.62.0"
  }
}
```

[top](#index)

### Example Usage

```terraform
module "google_data_catalog_tag_template_iam_binding" {
  source = "./modules/google/r/google_data_catalog_tag_template_iam_binding"

  # members - (required) is a type of set of string
  members = []
  # project - (optional) is a type of string
  project = null
  # region - (optional) is a type of string
  region = null
  # role - (required) is a type of string
  role = null
  # tag_template - (required) is a type of string
  tag_template = null

  condition = [{
    description = null
    expression  = null
    title       = null
  }]
}
```

[top](#index)

### Variables

```terraform
variable "members" {
  description = "(required)"
  type        = set(string)
}

variable "project" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "region" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "role" {
  description = "(required)"
  type        = string
}

variable "tag_template" {
  description = "(required)"
  type        = string
}

variable "condition" {
  description = "nested block: NestingList, min items: 0, max items: 1"
  type = set(object(
    {
      description = string
      expression  = string
      title       = string
    }
  ))
  default = []
}
```

[top](#index)

### Resource

```terraform
resource "google_data_catalog_tag_template_iam_binding" "this" {
  members      = var.members
  project      = var.project
  region       = var.region
  role         = var.role
  tag_template = var.tag_template

  dynamic "condition" {
    for_each = var.condition
    content {
      description = condition.value["description"]
      expression  = condition.value["expression"]
      title       = condition.value["title"]
    }
  }

}
```

[top](#index)

### Outputs

```terraform
output "etag" {
  description = "returns a string"
  value       = google_data_catalog_tag_template_iam_binding.this.etag
}

output "id" {
  description = "returns a string"
  value       = google_data_catalog_tag_template_iam_binding.this.id
}

output "project" {
  description = "returns a string"
  value       = google_data_catalog_tag_template_iam_binding.this.project
}

output "region" {
  description = "returns a string"
  value       = google_data_catalog_tag_template_iam_binding.this.region
}

output "this" {
  value = google_data_catalog_tag_template_iam_binding.this
}
```

[top](#index)