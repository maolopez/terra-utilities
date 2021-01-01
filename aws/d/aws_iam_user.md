# aws_iam_user
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
module "aws_iam_user" {
  source = "./modules/aws/d/aws_iam_user"

  # user_name - (required) is a type of string
  user_name = null
}
```
[top](#index)
### Variables
```hcl
variable "user_name" {
  description = "(required)"
  type        = string
}
```
[top](#index)

### Datasource
```hcl
data "aws_iam_user" "this" {
  user_name = var.user_name
}
```
[top](#index)
### Outputs
```hcl
output "arn" {
  description = "returns a string"
  value       = data.aws_iam_user.this.arn
}

output "id" {
  description = "returns a string"
  value       = data.aws_iam_user.this.id
}

output "path" {
  description = "returns a string"
  value       = data.aws_iam_user.this.path
}

output "permissions_boundary" {
  description = "returns a string"
  value       = data.aws_iam_user.this.permissions_boundary
}

output "user_id" {
  description = "returns a string"
  value       = data.aws_iam_user.this.user_id
}

output "this" {
  value = aws_iam_user.this
}
```
[top](#index)