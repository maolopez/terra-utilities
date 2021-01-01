# google_app_engine_application_url_dispatch_rules

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
module "google_app_engine_application_url_dispatch_rules" {
  source = "./modules/google/r/google_app_engine_application_url_dispatch_rules"

  # project - (optional) is a type of string
  project = null

  dispatch_rules = [{
    domain  = null
    path    = null
    service = null
  }]

  timeouts = [{
    create = null
    delete = null
    update = null
  }]
}
```

[top](#index)

### Variables

```hcl
variable "project" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "dispatch_rules" {
  description = "nested mode: NestingList, min items: 1, max items: 0"
  type = set(object(
    {
      domain  = string
      path    = string
      service = string
    }
  ))
}

variable "timeouts" {
  description = "nested mode: NestingSingle, min items: 0, max items: 0"
  type = set(object(
    {
      create = string
      delete = string
      update = string
    }
  ))
  default = []
}
```

[top](#index)

### Resource

```hcl
resource "google_app_engine_application_url_dispatch_rules" "this" {
  project = var.project

  dynamic "dispatch_rules" {
    for_each = var.dispatch_rules
    content {
      domain  = dispatch_rules.value["domain"]
      path    = dispatch_rules.value["path"]
      service = dispatch_rules.value["service"]
    }
  }

  dynamic "timeouts" {
    for_each = var.timeouts
    content {
      create = timeouts.value["create"]
      delete = timeouts.value["delete"]
      update = timeouts.value["update"]
    }
  }

}
```

[top](#index)

### Outputs

```hcl
output "id" {
  description = "returns a string"
  value       = google_app_engine_application_url_dispatch_rules.this.id
}

output "project" {
  description = "returns a string"
  value       = google_app_engine_application_url_dispatch_rules.this.project
}

output "this" {
  value = google_app_engine_application_url_dispatch_rules.this
}
```

[top](#index)