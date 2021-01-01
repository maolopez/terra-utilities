# aws_storagegateway_nfs_file_share
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
module "aws_storagegateway_nfs_file_share" {
  source = "./modules/aws/r/aws_storagegateway_nfs_file_share"

  # client_list - (required) is a type of set of string
  client_list = []
  # default_storage_class - (optional) is a type of string
  default_storage_class = null
  # file_share_name - (optional) is a type of string
  file_share_name = null
  # gateway_arn - (required) is a type of string
  gateway_arn = null
  # guess_mime_type_enabled - (optional) is a type of bool
  guess_mime_type_enabled = null
  # kms_encrypted - (optional) is a type of bool
  kms_encrypted = null
  # kms_key_arn - (optional) is a type of string
  kms_key_arn = null
  # location_arn - (required) is a type of string
  location_arn = null
  # notification_policy - (optional) is a type of string
  notification_policy = null
  # object_acl - (optional) is a type of string
  object_acl = null
  # read_only - (optional) is a type of bool
  read_only = null
  # requester_pays - (optional) is a type of bool
  requester_pays = null
  # role_arn - (required) is a type of string
  role_arn = null
  # squash - (optional) is a type of string
  squash = null
  # tags - (optional) is a type of map of string
  tags = {}

  cache_attributes = [{
    cache_stale_timeout_in_seconds = null
  }]

  nfs_file_share_defaults = [{
    directory_mode = null
    file_mode      = null
    group_id       = null
    owner_id       = null
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
variable "client_list" {
  description = "(required)"
  type        = set(string)
}

variable "default_storage_class" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "file_share_name" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "gateway_arn" {
  description = "(required)"
  type        = string
}

variable "guess_mime_type_enabled" {
  description = "(optional)"
  type        = bool
  default     = null
}

variable "kms_encrypted" {
  description = "(optional)"
  type        = bool
  default     = null
}

variable "kms_key_arn" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "location_arn" {
  description = "(required)"
  type        = string
}

variable "notification_policy" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "object_acl" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "read_only" {
  description = "(optional)"
  type        = bool
  default     = null
}

variable "requester_pays" {
  description = "(optional)"
  type        = bool
  default     = null
}

variable "role_arn" {
  description = "(required)"
  type        = string
}

variable "squash" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "tags" {
  description = "(optional)"
  type        = map(string)
  default     = null
}

variable "cache_attributes" {
  description = "nested mode: NestingList, min items: 0, max items: 1"
  type = set(object(
    {
      cache_stale_timeout_in_seconds = number
    }
  ))
  default = []
}

variable "nfs_file_share_defaults" {
  description = "nested mode: NestingList, min items: 0, max items: 1"
  type = set(object(
    {
      directory_mode = string
      file_mode      = string
      group_id       = string
      owner_id       = string
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
resource "aws_storagegateway_nfs_file_share" "this" {
  client_list             = var.client_list
  default_storage_class   = var.default_storage_class
  file_share_name         = var.file_share_name
  gateway_arn             = var.gateway_arn
  guess_mime_type_enabled = var.guess_mime_type_enabled
  kms_encrypted           = var.kms_encrypted
  kms_key_arn             = var.kms_key_arn
  location_arn            = var.location_arn
  notification_policy     = var.notification_policy
  object_acl              = var.object_acl
  read_only               = var.read_only
  requester_pays          = var.requester_pays
  role_arn                = var.role_arn
  squash                  = var.squash
  tags                    = var.tags

  dynamic "cache_attributes" {
    for_each = var.cache_attributes
    content {
      cache_stale_timeout_in_seconds = cache_attributes.value["cache_stale_timeout_in_seconds"]
    }
  }

  dynamic "nfs_file_share_defaults" {
    for_each = var.nfs_file_share_defaults
    content {
      directory_mode = nfs_file_share_defaults.value["directory_mode"]
      file_mode      = nfs_file_share_defaults.value["file_mode"]
      group_id       = nfs_file_share_defaults.value["group_id"]
      owner_id       = nfs_file_share_defaults.value["owner_id"]
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
output "arn" {
  description = "returns a string"
  value       = aws_storagegateway_nfs_file_share.this.arn
}

output "file_share_name" {
  description = "returns a string"
  value       = aws_storagegateway_nfs_file_share.this.file_share_name
}

output "fileshare_id" {
  description = "returns a string"
  value       = aws_storagegateway_nfs_file_share.this.fileshare_id
}

output "id" {
  description = "returns a string"
  value       = aws_storagegateway_nfs_file_share.this.id
}

output "path" {
  description = "returns a string"
  value       = aws_storagegateway_nfs_file_share.this.path
}

output "this" {
  value = aws_storagegateway_nfs_file_share.this
}
```
[top](#index)