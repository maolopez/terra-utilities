# google_dataproc_job_iam_member

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
module "google_dataproc_job_iam_member" {
  source = "./modules/google/r/google_dataproc_job_iam_member"

  # job_id - (required) is a type of string
  job_id = null
  # member - (required) is a type of string
  member = null
  # project - (optional) is a type of string
  project = null
  # region - (optional) is a type of string
  region = null
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
variable "job_id" {
  description = "(required)"
  type        = string
}

variable "member" {
  description = "(required)"
  type        = string
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
resource "google_dataproc_job_iam_member" "this" {
  job_id  = var.job_id
  member  = var.member
  project = var.project
  region  = var.region
  role    = var.role

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
  value       = google_dataproc_job_iam_member.this.etag
}

output "id" {
  description = "returns a string"
  value       = google_dataproc_job_iam_member.this.id
}

output "project" {
  description = "returns a string"
  value       = google_dataproc_job_iam_member.this.project
}

output "region" {
  description = "returns a string"
  value       = google_dataproc_job_iam_member.this.region
}

output "this" {
  value = google_dataproc_job_iam_member.this
}
```

[top](#index)