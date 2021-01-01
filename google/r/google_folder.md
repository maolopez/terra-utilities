# google_folder

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
module "google_folder" {
  source = "./modules/google/r/google_folder"

  # display_name - (required) is a type of string
  display_name = null
  # parent - (required) is a type of string
  parent = null

  timeouts = [{
    create = null
    delete = null
    read   = null
    update = null
  }]
}
```

[top](#index)

### Variables

```hcl
variable "display_name" {
  description = "(required) - The folder's display name. A folder's display name must be unique amongst its siblings, e.g. no two folders with the same parent can share the same display name. The display name must start and end with a letter or digit, may contain letters, digits, spaces, hyphens and underscores and can be no longer than 30 characters."
  type        = string
}

variable "parent" {
  description = "(required) - The resource name of the parent Folder or Organization. Must be of the form folders/{folder_id} or organizations/{org_id}."
  type        = string
}

variable "timeouts" {
  description = "nested mode: NestingSingle, min items: 0, max items: 0"
  type = set(object(
    {
      create = string
      delete = string
      read   = string
      update = string
    }
  ))
  default = []
}
```

[top](#index)

### Resource

```hcl
resource "google_folder" "this" {
  display_name = var.display_name
  parent       = var.parent

  dynamic "timeouts" {
    for_each = var.timeouts
    content {
      create = timeouts.value["create"]
      delete = timeouts.value["delete"]
      read   = timeouts.value["read"]
      update = timeouts.value["update"]
    }
  }

}
```

[top](#index)

### Outputs

```hcl
output "create_time" {
  description = "returns a string"
  value       = google_folder.this.create_time
}

output "folder_id" {
  description = "returns a string"
  value       = google_folder.this.folder_id
}

output "id" {
  description = "returns a string"
  value       = google_folder.this.id
}

output "lifecycle_state" {
  description = "returns a string"
  value       = google_folder.this.lifecycle_state
}

output "name" {
  description = "returns a string"
  value       = google_folder.this.name
}

output "this" {
  value = google_folder.this
}
```

[top](#index)