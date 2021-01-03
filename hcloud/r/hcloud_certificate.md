# hcloud_certificate

[back](../hcloud.md)

### Index

- [Example Usage](#example-usage)
- [Variables](#variables)
- [Resource](#resource)
- [Outputs](#outputs)

### Terraform

```terraform
terraform {
  required_providers {
    hcloud = ">= 1.23.0"
  }
}
```

[top](#index)

### Example Usage

```terraform
module "hcloud_certificate" {
  source = "./modules/hcloud/r/hcloud_certificate"

  # certificate - (required) is a type of string
  certificate = null
  # labels - (optional) is a type of map of string
  labels = {}
  # name - (required) is a type of string
  name = null
  # private_key - (required) is a type of string
  private_key = null
}
```

[top](#index)

### Variables

```terraform
variable "certificate" {
  description = "(required)"
  type        = string
}

variable "labels" {
  description = "(optional)"
  type        = map(string)
  default     = null
}

variable "name" {
  description = "(required)"
  type        = string
}

variable "private_key" {
  description = "(required)"
  type        = string
}
```

[top](#index)

### Resource

```terraform
resource "hcloud_certificate" "this" {
  certificate = var.certificate
  labels      = var.labels
  name        = var.name
  private_key = var.private_key
}
```

[top](#index)

### Outputs

```terraform
output "created" {
  description = "returns a string"
  value       = hcloud_certificate.this.created
}

output "domain_names" {
  description = "returns a list of string"
  value       = hcloud_certificate.this.domain_names
}

output "fingerprint" {
  description = "returns a string"
  value       = hcloud_certificate.this.fingerprint
}

output "id" {
  description = "returns a string"
  value       = hcloud_certificate.this.id
}

output "not_valid_after" {
  description = "returns a string"
  value       = hcloud_certificate.this.not_valid_after
}

output "not_valid_before" {
  description = "returns a string"
  value       = hcloud_certificate.this.not_valid_before
}

output "this" {
  value = hcloud_certificate.this
}
```

[top](#index)