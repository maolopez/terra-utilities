# google_bigquery_table_iam_binding

[back](../google.md)

### Index

- [Example Usage](#example-usage)
- [Variables](#variables)
- [Datasource](#datasource)
- [Outputs](#outputs)

### Terraform

```hcl
terraform {
  required_providers {
    google = ">= 3.51.0"
  }
}
```

[top](#index)

### Example Usage

```hcl
module "google_bigquery_table_iam_binding" {
  source = "./modules/google/r/google_bigquery_table_iam_binding"

  # dataset_id - (required) is a type of string
  dataset_id = null
  # members - (required) is a type of set of string
  members = []
  # project - (optional) is a type of string
  project = null
  # role - (required) is a type of string
  role = null
  # table_id - (required) is a type of string
  table_id = null

  condition = [{
    description = null
    expression  = null
    title       = null
  }]
}
```

[top](#index)

### Variables

```hcl
variable "dataset_id" {
  description = "(required)"
  type        = string
}

variable "members" {
  description = "(required)"
  type        = set(string)
}

variable "project" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "role" {
  description = "(required)"
  type        = string
}

variable "table_id" {
  description = "(required)"
  type        = string
}

variable "condition" {
  description = "nested mode: NestingList, min items: 0, max items: 1"
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

```hcl
resource "google_bigquery_table_iam_binding" "this" {
  dataset_id = var.dataset_id
  members    = var.members
  project    = var.project
  role       = var.role
  table_id   = var.table_id

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

```hcl
output "etag" {
  description = "returns a string"
  value       = google_bigquery_table_iam_binding.this.etag
}

output "id" {
  description = "returns a string"
  value       = google_bigquery_table_iam_binding.this.id
}

output "project" {
  description = "returns a string"
  value       = google_bigquery_table_iam_binding.this.project
}

output "this" {
  value = google_bigquery_table_iam_binding.this
}
```

[top](#index)