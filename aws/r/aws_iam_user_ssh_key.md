# aws_iam_user_ssh_key
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
module "aws_iam_user_ssh_key" {
  source = "./modules/aws/r/aws_iam_user_ssh_key"

  # encoding - (required) is a type of string
  encoding = null
  # public_key - (required) is a type of string
  public_key = null
  # status - (optional) is a type of string
  status = null
  # username - (required) is a type of string
  username = null
}
```
[top](#index)
### Variables
```hcl
variable "encoding" {
  description = "(required)"
  type        = string
}

variable "public_key" {
  description = "(required)"
  type        = string
}

variable "status" {
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

### Resource
```hcl
resource "aws_iam_user_ssh_key" "this" {
  encoding   = var.encoding
  public_key = var.public_key
  status     = var.status
  username   = var.username
}
```
[top](#index)
### Outputs
```hcl
output "fingerprint" {
  description = "returns a string"
  value       = aws_iam_user_ssh_key.this.fingerprint
}

output "id" {
  description = "returns a string"
  value       = aws_iam_user_ssh_key.this.id
}

output "ssh_public_key_id" {
  description = "returns a string"
  value       = aws_iam_user_ssh_key.this.ssh_public_key_id
}

output "status" {
  description = "returns a string"
  value       = aws_iam_user_ssh_key.this.status
}

output "this" {
  value = aws_iam_user_ssh_key.this
}
```
[top](#index)