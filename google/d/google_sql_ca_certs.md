# google_sql_ca_certs

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
module "google_sql_ca_certs" {
  source = "./modules/google/d/google_sql_ca_certs"

  # instance - (required) is a type of string
  instance = null
  # project - (optional) is a type of string
  project = null
}
```

[top](#index)

### Variables

```hcl
variable "instance" {
  description = "(required)"
  type        = string
}

variable "project" {
  description = "(optional)"
  type        = string
  default     = null
}
```

[top](#index)

### Datasource

```hcl
data "google_sql_ca_certs" "this" {
  instance = var.instance
  project  = var.project
}
```

[top](#index)

### Outputs

```hcl
output "active_version" {
  description = "returns a string"
  value       = data.google_sql_ca_certs.this.active_version
}

output "certs" {
  description = "returns a list of object"
  value       = data.google_sql_ca_certs.this.certs
}

output "id" {
  description = "returns a string"
  value       = data.google_sql_ca_certs.this.id
}

output "project" {
  description = "returns a string"
  value       = data.google_sql_ca_certs.this.project
}

output "this" {
  value = google_sql_ca_certs.this
}
```

[top](#index)