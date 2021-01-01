# aws_backup_vault_policy
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
module "aws_backup_vault_policy" {
  source = "./modules/aws/r/aws_backup_vault_policy"

  # backup_vault_name - (required) is a type of string
  backup_vault_name = null
  # policy - (required) is a type of string
  policy = null
}
```
[top](#index)
### Variables
```hcl
variable "backup_vault_name" {
  description = "(required)"
  type        = string
}

variable "policy" {
  description = "(required)"
  type        = string
}
```
[top](#index)

### Resource
```hcl
resource "aws_backup_vault_policy" "this" {
  backup_vault_name = var.backup_vault_name
  policy            = var.policy
}
```
[top](#index)
### Outputs
```hcl
output "backup_vault_arn" {
  description = "returns a string"
  value       = aws_backup_vault_policy.this.backup_vault_arn
}

output "id" {
  description = "returns a string"
  value       = aws_backup_vault_policy.this.id
}

output "this" {
  value = aws_backup_vault_policy.this
}
```
[top](#index)