# github_collaborators

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
module "github_collaborators" {
  source = "./modules/github/d/github_collaborators"

  # affiliation - (optional) is a type of string
  affiliation = null
  # owner - (required) is a type of string
  owner = null
  # repository - (required) is a type of string
  repository = null
}
```

[top](#index)

### Variables

```hcl
variable "affiliation" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "owner" {
  description = "(required)"
  type        = string
}

variable "repository" {
  description = "(required)"
  type        = string
}
```

[top](#index)

### Datasource

```hcl
data "github_collaborators" "this" {
  affiliation = var.affiliation
  owner       = var.owner
  repository  = var.repository
}
```

[top](#index)

### Outputs

```hcl
output "collaborator" {
  description = "returns a list of object"
  value       = data.github_collaborators.this.collaborator
}

output "id" {
  description = "returns a string"
  value       = data.github_collaborators.this.id
}

output "this" {
  value = github_collaborators.this
}
```

[top](#index)