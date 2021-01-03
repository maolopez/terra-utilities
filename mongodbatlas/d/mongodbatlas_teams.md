# mongodbatlas_teams

[back](../mongodbatlas.md)

### Index

- [Example Usage](#example-usage)
- [Variables](#variables)
- [Datasource](#datasource)
- [Outputs](#outputs)

### Terraform

```terraform
terraform {
  required_providers {
    mongodbatlas = ">= 0.7.0"
  }
}
```

[top](#index)

### Example Usage

```terraform
module "mongodbatlas_teams" {
  source = "./modules/mongodbatlas/d/mongodbatlas_teams"

  # name - (optional) is a type of string
  name = null
  # org_id - (required) is a type of string
  org_id = null
  # team_id - (optional) is a type of string
  team_id = null
}
```

[top](#index)

### Variables

```terraform
variable "name" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "org_id" {
  description = "(required)"
  type        = string
}

variable "team_id" {
  description = "(optional)"
  type        = string
  default     = null
}
```

[top](#index)

### Datasource

```terraform
data "mongodbatlas_teams" "this" {
  name    = var.name
  org_id  = var.org_id
  team_id = var.team_id
}
```

[top](#index)

### Outputs

```terraform
output "id" {
  description = "returns a string"
  value       = data.mongodbatlas_teams.this.id
}

output "name" {
  description = "returns a string"
  value       = data.mongodbatlas_teams.this.name
}

output "team_id" {
  description = "returns a string"
  value       = data.mongodbatlas_teams.this.team_id
}

output "usernames" {
  description = "returns a set of string"
  value       = data.mongodbatlas_teams.this.usernames
}

output "this" {
  value = mongodbatlas_teams.this
}
```

[top](#index)