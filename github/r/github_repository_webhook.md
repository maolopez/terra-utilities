# github_repository_webhook

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
module "github_repository_webhook" {
  source = "./modules/github/r/github_repository_webhook"

  # active - (optional) is a type of bool
  active = null
  # events - (required) is a type of set of string
  events = []
  # name - (optional) is a type of string
  name = null
  # repository - (required) is a type of string
  repository = null

  configuration = [{
    content_type = null
    insecure_ssl = null
    secret       = null
    url          = null
  }]
}
```

[top](#index)

### Variables

```hcl
variable "active" {
  description = "(optional)"
  type        = bool
  default     = null
}

variable "events" {
  description = "(required)"
  type        = set(string)
}

variable "name" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "repository" {
  description = "(required)"
  type        = string
}

variable "configuration" {
  description = "nested mode: NestingList, min items: 0, max items: 1"
  type = set(object(
    {
      content_type = string
      insecure_ssl = bool
      secret       = string
      url          = string
    }
  ))
  default = []
}
```

[top](#index)

### Resource

```hcl
resource "github_repository_webhook" "this" {
  active     = var.active
  events     = var.events
  name       = var.name
  repository = var.repository

  dynamic "configuration" {
    for_each = var.configuration
    content {
      content_type = configuration.value["content_type"]
      insecure_ssl = configuration.value["insecure_ssl"]
      secret       = configuration.value["secret"]
      url          = configuration.value["url"]
    }
  }

}
```

[top](#index)

### Outputs

```hcl
output "etag" {
  description = "returns a string"
  value       = github_repository_webhook.this.etag
}

output "id" {
  description = "returns a string"
  value       = github_repository_webhook.this.id
}

output "url" {
  description = "returns a string"
  value       = github_repository_webhook.this.url
}

output "this" {
  value = github_repository_webhook.this
}
```

[top](#index)