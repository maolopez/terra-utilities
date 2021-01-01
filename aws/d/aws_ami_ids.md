# aws_ami_ids
[back](../aws.md)
### Index
- [Example Usage](#example-usage)
- [Variables](#variables)
- [Datasource](#datasource)
- [Outputs](#outputs)
### Terraform
```hcl
terraform {
  required_providers {
    aws = ">= 3.22.0"
  }
}
```
[top](#index)
### Example Usage
```hcl
module "aws_ami_ids" {
  source = "./modules/aws/d/aws_ami_ids"

  # executable_users - (optional) is a type of list of string
  executable_users = []
  # name_regex - (optional) is a type of string
  name_regex = null
  # owners - (required) is a type of list of string
  owners = []
  # sort_ascending - (optional) is a type of bool
  sort_ascending = null

  filter = [{
    name   = null
    values = []
  }]
}
```
[top](#index)
### Variables
```hcl
variable "executable_users" {
  description = "(optional)"
  type        = list(string)
  default     = null
}

variable "name_regex" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "owners" {
  description = "(required)"
  type        = list(string)
}

variable "sort_ascending" {
  description = "(optional)"
  type        = bool
  default     = null
}

variable "filter" {
  description = "nested mode: NestingSet, min items: 0, max items: 0"
  type = set(object(
    {
      name   = string
      values = list(string)
    }
  ))
  default = []
}
```
[top](#index)

### Datasource
```hcl
data "aws_ami_ids" "this" {
  executable_users = var.executable_users
  name_regex       = var.name_regex
  owners           = var.owners
  sort_ascending   = var.sort_ascending

  dynamic "filter" {
    for_each = var.filter
    content {
      name   = filter.value["name"]
      values = filter.value["values"]
    }
  }

}
```
[top](#index)
### Outputs
```hcl
output "id" {
  description = "returns a string"
  value       = data.aws_ami_ids.this.id
}

output "ids" {
  description = "returns a list of string"
  value       = data.aws_ami_ids.this.ids
}

output "this" {
  value = aws_ami_ids.this
}
```
[top](#index)