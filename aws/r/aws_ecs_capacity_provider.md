# aws_ecs_capacity_provider
[back](../aws.md)
### Index
- [Example Usage](#example-usage)
- [Variables](#variables)
- [Resource](#resource)
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
module "aws_ecs_capacity_provider" {
  source = "./modules/aws/r/aws_ecs_capacity_provider"

  # name - (required) is a type of string
  name = null
  # tags - (optional) is a type of map of string
  tags = {}

  auto_scaling_group_provider = [{
    auto_scaling_group_arn = null
    managed_scaling = [{
      maximum_scaling_step_size = null
      minimum_scaling_step_size = null
      status                    = null
      target_capacity           = null
    }]
    managed_termination_protection = null
  }]
}
```
[top](#index)
### Variables
```hcl
variable "name" {
  description = "(required)"
  type        = string
}

variable "tags" {
  description = "(optional)"
  type        = map(string)
  default     = null
}

variable "auto_scaling_group_provider" {
  description = "nested mode: NestingList, min items: 1, max items: 1"
  type = set(object(
    {
      auto_scaling_group_arn = string
      managed_scaling = list(object(
        {
          maximum_scaling_step_size = number
          minimum_scaling_step_size = number
          status                    = string
          target_capacity           = number
        }
      ))
      managed_termination_protection = string
    }
  ))
}
```
[top](#index)

### Resource
```hcl
resource "aws_ecs_capacity_provider" "this" {
  name = var.name
  tags = var.tags

  dynamic "auto_scaling_group_provider" {
    for_each = var.auto_scaling_group_provider
    content {
      auto_scaling_group_arn         = auto_scaling_group_provider.value["auto_scaling_group_arn"]
      managed_termination_protection = auto_scaling_group_provider.value["managed_termination_protection"]

      dynamic "managed_scaling" {
        for_each = auto_scaling_group_provider.value.managed_scaling
        content {
          maximum_scaling_step_size = managed_scaling.value["maximum_scaling_step_size"]
          minimum_scaling_step_size = managed_scaling.value["minimum_scaling_step_size"]
          status                    = managed_scaling.value["status"]
          target_capacity           = managed_scaling.value["target_capacity"]
        }
      }

    }
  }

}
```
[top](#index)
### Outputs
```hcl
output "arn" {
  description = "returns a string"
  value       = aws_ecs_capacity_provider.this.arn
}

output "id" {
  description = "returns a string"
  value       = aws_ecs_capacity_provider.this.id
}

output "this" {
  value = aws_ecs_capacity_provider.this
}
```
[top](#index)