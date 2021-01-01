# github_membership

[back](../github.md)

### Index

- [Example Usage](#example-usage)
- [Variables](#variables)
- [Datasource](#datasource)
- [Outputs](#outputs)

### Terraform

```hcl
terraform {
  required_providers {
    github = ">= 4.1.0"
  }
}
```

[top](#index)

### Example Usage

```hcl
module "github_membership" {
  source = "./modules/github/d/github_membership"

  # organization - (optional) is a type of string
  organization = null
  # username - (required) is a type of string
  username = null
}
```

[top](#index)

### Variables

```hcl
variable "organization" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "username" {
  description = "(required)"
  type        = string
}
```

[top](#index)

### Datasource

```hcl
data "github_membership" "this" {
  organization = var.organization
  username     = var.username
}
```

[top](#index)

### Outputs

```hcl
output "etag" {
  description = "returns a string"
  value       = data.github_membership.this.etag
}

output "id" {
  description = "returns a string"
  value       = data.github_membership.this.id
}

output "role" {
  description = "returns a string"
  value       = data.github_membership.this.role
}

output "this" {
  value = github_membership.this
}
```

[top](#index)