# google_sourcerepo_repository_iam_binding

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
module "google_sourcerepo_repository_iam_binding" {
  source = "./modules/google/r/google_sourcerepo_repository_iam_binding"

  # members - (required) is a type of set of string
  members = []
  # project - (optional) is a type of string
  project = null
  # repository - (required) is a type of string
  repository = null
  # role - (required) is a type of string
  role = null

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
variable "members" {
  description = "(required)"
  type        = set(string)
}

variable "project" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "repository" {
  description = "(required)"
  type        = string
}

variable "role" {
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
resource "google_sourcerepo_repository_iam_binding" "this" {
  members    = var.members
  project    = var.project
  repository = var.repository
  role       = var.role

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
  value       = google_sourcerepo_repository_iam_binding.this.etag
}

output "id" {
  description = "returns a string"
  value       = google_sourcerepo_repository_iam_binding.this.id
}

output "project" {
  description = "returns a string"
  value       = google_sourcerepo_repository_iam_binding.this.project
}

output "this" {
  value = google_sourcerepo_repository_iam_binding.this
}
```

[top](#index)