# google_compute_regions

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
module "google_compute_regions" {
  source = "./modules/google/d/google_compute_regions"

  # project - (optional) is a type of string
  project = null
  # status - (optional) is a type of string
  status = null
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

variable "status" {
  description = "(optional)"
  type        = string
  default     = null
}
```

[top](#index)

### Datasource

```hcl
data "google_compute_regions" "this" {
  project = var.project
  status  = var.status
}
```

[top](#index)

### Outputs

```hcl
output "id" {
  description = "returns a string"
  value       = data.google_compute_regions.this.id
}

output "names" {
  description = "returns a list of string"
  value       = data.google_compute_regions.this.names
}

output "project" {
  description = "returns a string"
  value       = data.google_compute_regions.this.project
}

output "this" {
  value = google_compute_regions.this
}
```

[top](#index)