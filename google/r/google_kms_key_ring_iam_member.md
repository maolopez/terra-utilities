# google_kms_key_ring_iam_member

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
module "google_kms_key_ring_iam_member" {
  source = "./modules/google/r/google_kms_key_ring_iam_member"

  # key_ring_id - (required) is a type of string
  key_ring_id = null
  # member - (required) is a type of string
  member = null
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
variable "key_ring_id" {
  description = "(required)"
  type        = string
}

variable "member" {
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
resource "google_kms_key_ring_iam_member" "this" {
  key_ring_id = var.key_ring_id
  member      = var.member
  role        = var.role

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
  value       = google_kms_key_ring_iam_member.this.etag
}

output "id" {
  description = "returns a string"
  value       = google_kms_key_ring_iam_member.this.id
}

output "this" {
  value = google_kms_key_ring_iam_member.this
}
```

[top](#index)