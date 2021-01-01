# aws_ami_copy
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
module "aws_ami_copy" {
  source = "./modules/aws/r/aws_ami_copy"

  # description - (optional) is a type of string
  description = null
  # encrypted - (optional) is a type of bool
  encrypted = null
  # kms_key_id - (optional) is a type of string
  kms_key_id = null
  # name - (required) is a type of string
  name = null
  # source_ami_id - (required) is a type of string
  source_ami_id = null
  # source_ami_region - (required) is a type of string
  source_ami_region = null
  # tags - (optional) is a type of map of string
  tags = {}

  ebs_block_device = [{
    delete_on_termination = null
    device_name           = null
    encrypted             = null
    iops                  = null
    snapshot_id           = null
    volume_size           = null
    volume_type           = null
  }]

  ephemeral_block_device = [{
    device_name  = null
    virtual_name = null
  }]

  timeouts = [{
    create = null
    delete = null
    update = null
  }]
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

variable "encrypted" {
  description = "(optional)"
  type        = bool
  default     = null
}

variable "kms_key_id" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "name" {
  description = "(required)"
  type        = string
}

variable "source_ami_id" {
  description = "(required)"
  type        = string
}

variable "source_ami_region" {
  description = "(required)"
  type        = string
}

variable "tags" {
  description = "(optional)"
  type        = map(string)
  default     = null
}

variable "ebs_block_device" {
  description = "nested mode: NestingSet, min items: 0, max items: 0"
  type = set(object(
    {
      delete_on_termination = bool
      device_name           = string
      encrypted             = bool
      iops                  = number
      snapshot_id           = string
      volume_size           = number
      volume_type           = string
    }
  ))
  default = []
}

variable "ephemeral_block_device" {
  description = "nested mode: NestingSet, min items: 0, max items: 0"
  type = set(object(
    {
      device_name  = string
      virtual_name = string
    }
  ))
  default = []
}

variable "timeouts" {
  description = "nested mode: NestingSingle, min items: 0, max items: 0"
  type = set(object(
    {
      create = string
      delete = string
      update = string
    }
  ))
  default = []
}
```
[top](#index)

### Resource
```hcl
resource "aws_ami_copy" "this" {
  description       = var.description
  encrypted         = var.encrypted
  kms_key_id        = var.kms_key_id
  name              = var.name
  source_ami_id     = var.source_ami_id
  source_ami_region = var.source_ami_region
  tags              = var.tags

  dynamic "ebs_block_device" {
    for_each = var.ebs_block_device
    content {
    }
  }

  dynamic "ephemeral_block_device" {
    for_each = var.ephemeral_block_device
    content {
    }
  }

  dynamic "timeouts" {
    for_each = var.timeouts
    content {
      create = timeouts.value["create"]
      delete = timeouts.value["delete"]
      update = timeouts.value["update"]
    }
  }

}
```
[top](#index)
### Outputs
```hcl
output "architecture" {
  description = "returns a string"
  value       = aws_ami_copy.this.architecture
}

output "arn" {
  description = "returns a string"
  value       = aws_ami_copy.this.arn
}

output "ena_support" {
  description = "returns a bool"
  value       = aws_ami_copy.this.ena_support
}

output "id" {
  description = "returns a string"
  value       = aws_ami_copy.this.id
}

output "image_location" {
  description = "returns a string"
  value       = aws_ami_copy.this.image_location
}

output "kernel_id" {
  description = "returns a string"
  value       = aws_ami_copy.this.kernel_id
}

output "kms_key_id" {
  description = "returns a string"
  value       = aws_ami_copy.this.kms_key_id
}

output "manage_ebs_snapshots" {
  description = "returns a bool"
  value       = aws_ami_copy.this.manage_ebs_snapshots
}

output "ramdisk_id" {
  description = "returns a string"
  value       = aws_ami_copy.this.ramdisk_id
}

output "root_device_name" {
  description = "returns a string"
  value       = aws_ami_copy.this.root_device_name
}

output "root_snapshot_id" {
  description = "returns a string"
  value       = aws_ami_copy.this.root_snapshot_id
}

output "sriov_net_support" {
  description = "returns a string"
  value       = aws_ami_copy.this.sriov_net_support
}

output "virtualization_type" {
  description = "returns a string"
  value       = aws_ami_copy.this.virtualization_type
}

output "this" {
  value = aws_ami_copy.this
}
```
[top](#index)