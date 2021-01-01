# google_compute_shared_vpc_host_project

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
module "google_compute_shared_vpc_host_project" {
  source = "./modules/google/r/google_compute_shared_vpc_host_project"

  # project - (required) is a type of string
  project = null

  timeouts = [{
    create = null
    delete = null
  }]
}
```

[top](#index)

### Variables

```hcl
variable "project" {
  description = "(required) - The ID of the project that will serve as a Shared VPC host project"
  type        = string
}

variable "timeouts" {
  description = "nested mode: NestingSingle, min items: 0, max items: 0"
  type = set(object(
    {
      create = string
      delete = string
    }
  ))
  default = []
}
```

[top](#index)

### Resource

```hcl
resource "google_compute_shared_vpc_host_project" "this" {
  project = var.project

  dynamic "timeouts" {
    for_each = var.timeouts
    content {
      create = timeouts.value["create"]
      delete = timeouts.value["delete"]
    }
  }

}
```

[top](#index)

### Outputs

```hcl
output "id" {
  description = "returns a string"
  value       = google_compute_shared_vpc_host_project.this.id
}

output "this" {
  value = google_compute_shared_vpc_host_project.this
}
```

[top](#index)