# aws_pinpoint_email_channel
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
module "aws_pinpoint_email_channel" {
  source = "./modules/aws/r/aws_pinpoint_email_channel"

  # application_id - (required) is a type of string
  application_id = null
  # enabled - (optional) is a type of bool
  enabled = null
  # from_address - (required) is a type of string
  from_address = null
  # identity - (required) is a type of string
  identity = null
  # role_arn - (required) is a type of string
  role_arn = null
}
```
[top](#index)
### Variables
```hcl
variable "application_id" {
  description = "(required)"
  type        = string
}

variable "enabled" {
  description = "(optional)"
  type        = bool
  default     = null
}

variable "from_address" {
  description = "(required)"
  type        = string
}

variable "identity" {
  description = "(required)"
  type        = string
}

variable "role_arn" {
  description = "(required)"
  type        = string
}
```
[top](#index)

### Resource
```hcl
resource "aws_pinpoint_email_channel" "this" {
  application_id = var.application_id
  enabled        = var.enabled
  from_address   = var.from_address
  identity       = var.identity
  role_arn       = var.role_arn
}
```
[top](#index)
### Outputs
```hcl
output "id" {
  description = "returns a string"
  value       = aws_pinpoint_email_channel.this.id
}

output "messages_per_second" {
  description = "returns a number"
  value       = aws_pinpoint_email_channel.this.messages_per_second
}

output "this" {
  value = aws_pinpoint_email_channel.this
}
```
[top](#index)