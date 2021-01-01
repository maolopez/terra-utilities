# aws_vpc_endpoint_route_table_association
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
module "aws_vpc_endpoint_route_table_association" {
  source = "./modules/aws/r/aws_vpc_endpoint_route_table_association"

  # route_table_id - (required) is a type of string
  route_table_id = null
  # vpc_endpoint_id - (required) is a type of string
  vpc_endpoint_id = null
}
```
[top](#index)
### Variables
```hcl
variable "route_table_id" {
  description = "(required)"
  type        = string
}

variable "vpc_endpoint_id" {
  description = "(required)"
  type        = string
}
```
[top](#index)

### Resource
```hcl
resource "aws_vpc_endpoint_route_table_association" "this" {
  route_table_id  = var.route_table_id
  vpc_endpoint_id = var.vpc_endpoint_id
}
```
[top](#index)
### Outputs
```hcl
output "id" {
  description = "returns a string"
  value       = aws_vpc_endpoint_route_table_association.this.id
}

output "this" {
  value = aws_vpc_endpoint_route_table_association.this
}
```
[top](#index)