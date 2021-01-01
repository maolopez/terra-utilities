# aws_ami_from_instance
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
module "aws_ami_from_instance" {
  source = "./modules/aws/r/aws_ami_from_instance"

  # description - (optional) is a type of string
  description = null
  # name - (required) is a type of string
  name = null
  # snapshot_without_reboot - (optional) is a type of bool
  snapshot_without_reboot = null
  # source_instance_id - (required) is a type of string
  source_instance_id = null
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

variable "name" {
  description = "(required)"
  type        = string
}

variable "snapshot_without_reboot" {
  description = "(optional)"
  type        = bool
  default     = null
}

variable "source_instance_id" {
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
resource "aws_ami_from_instance" "this" {
  description             = var.description
  name                    = var.name
  snapshot_without_reboot = var.snapshot_without_reboot
  source_instance_id      = var.source_instance_id
  tags                    = var.tags

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
  value       = aws_ami_from_instance.this.architecture
}

output "arn" {
  description = "returns a string"
  value       = aws_ami_from_instance.this.arn
}

output "ena_support" {
  description = "returns a bool"
  value       = aws_ami_from_instance.this.ena_support
}

output "id" {
  description = "returns a string"
  value       = aws_ami_from_instance.this.id
}

output "image_location" {
  description = "returns a string"
  value       = aws_ami_from_instance.this.image_location
}

output "kernel_id" {
  description = "returns a string"
  value       = aws_ami_from_instance.this.kernel_id
}

output "manage_ebs_snapshots" {
  description = "returns a bool"
  value       = aws_ami_from_instance.this.manage_ebs_snapshots
}

output "ramdisk_id" {
  description = "returns a string"
  value       = aws_ami_from_instance.this.ramdisk_id
}

output "root_device_name" {
  description = "returns a string"
  value       = aws_ami_from_instance.this.root_device_name
}

output "root_snapshot_id" {
  description = "returns a string"
  value       = aws_ami_from_instance.this.root_snapshot_id
}

output "sriov_net_support" {
  description = "returns a string"
  value       = aws_ami_from_instance.this.sriov_net_support
}

output "virtualization_type" {
  description = "returns a string"
  value       = aws_ami_from_instance.this.virtualization_type
}

output "this" {
  value = aws_ami_from_instance.this
}
```
[top](#index)