# aws_route53_zone_association
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
module "aws_route53_zone_association" {
  source = "./modules/aws/r/aws_route53_zone_association"

  # vpc_id - (required) is a type of string
  vpc_id = null
  # vpc_region - (optional) is a type of string
  vpc_region = null
  # zone_id - (required) is a type of string
  zone_id = null
}
```
[top](#index)
### Variables
```hcl
variable "vpc_id" {
  description = "(required)"
  type        = string
}

variable "vpc_region" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "zone_id" {
  description = "(required)"
  type        = string
}
```
[top](#index)

### Resource
```hcl
resource "aws_route53_zone_association" "this" {
  vpc_id     = var.vpc_id
  vpc_region = var.vpc_region
  zone_id    = var.zone_id
}
```
[top](#index)
### Outputs
```hcl
output "id" {
  description = "returns a string"
  value       = aws_route53_zone_association.this.id
}

output "owning_account" {
  description = "returns a string"
  value       = aws_route53_zone_association.this.owning_account
}

output "vpc_region" {
  description = "returns a string"
  value       = aws_route53_zone_association.this.vpc_region
}

output "this" {
  value = aws_route53_zone_association.this
}
```
[top](#index)