# aws_snapshot_create_volume_permission
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
module "aws_snapshot_create_volume_permission" {
  source = "./modules/aws/r/aws_snapshot_create_volume_permission"

  # account_id - (required) is a type of string
  account_id = null
  # snapshot_id - (required) is a type of string
  snapshot_id = null
}
```
[top](#index)
### Variables
```hcl
variable "account_id" {
  description = "(required)"
  type        = string
}

variable "snapshot_id" {
  description = "(required)"
  type        = string
}
```
[top](#index)

### Resource
```hcl
resource "aws_snapshot_create_volume_permission" "this" {
  account_id  = var.account_id
  snapshot_id = var.snapshot_id
}
```
[top](#index)
### Outputs
```hcl
output "id" {
  description = "returns a string"
  value       = aws_snapshot_create_volume_permission.this.id
}

output "this" {
  value = aws_snapshot_create_volume_permission.this
}
```
[top](#index)