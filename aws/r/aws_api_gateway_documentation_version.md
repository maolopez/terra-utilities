# aws_api_gateway_documentation_version
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
module "aws_api_gateway_documentation_version" {
  source = "./modules/aws/r/aws_api_gateway_documentation_version"

  # description - (optional) is a type of string
  description = null
  # rest_api_id - (required) is a type of string
  rest_api_id = null
  # version - (required) is a type of string
  version = null
}
```
[top](#index)
### Variables
```hcl
variable "description" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "rest_api_id" {
  description = "(required)"
  type        = string
}

variable "version" {
  description = "(required)"
  type        = string
}
```
[top](#index)

### Resource
```hcl
resource "aws_api_gateway_documentation_version" "this" {
  description = var.description
  rest_api_id = var.rest_api_id
  version     = var.version
}
```
[top](#index)
### Outputs
```hcl
output "id" {
  description = "returns a string"
  value       = aws_api_gateway_documentation_version.this.id
}

output "this" {
  value = aws_api_gateway_documentation_version.this
}
```
[top](#index)