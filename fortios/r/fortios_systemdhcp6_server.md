# fortios_systemdhcp6_server

[back](../fortios.md)

### Index

- [Example Usage](#example-usage)
- [Variables](#variables)
- [Resource](#resource)
- [Outputs](#outputs)

### Terraform

```terraform
terraform {
  required_providers {
    fortios = ">= 1.6.18"
  }
}
```

[top](#index)

### Example Usage

```terraform
module "fortios_systemdhcp6_server" {
  source = "./modules/fortios/r/fortios_systemdhcp6_server"

  # dns_search_list - (optional) is a type of string
  dns_search_list = null
  # dns_server1 - (optional) is a type of string
  dns_server1 = null
  # dns_server2 - (optional) is a type of string
  dns_server2 = null
  # dns_server3 - (optional) is a type of string
  dns_server3 = null
  # dns_service - (optional) is a type of string
  dns_service = null
  # domain - (optional) is a type of string
  domain = null
  # fosid - (required) is a type of number
  fosid = null
  # interface - (required) is a type of string
  interface = null
  # ip_mode - (optional) is a type of string
  ip_mode = null
  # lease_time - (optional) is a type of number
  lease_time = null
  # option1 - (optional) is a type of string
  option1 = null
  # option2 - (optional) is a type of string
  option2 = null
  # option3 - (optional) is a type of string
  option3 = null
  # rapid_commit - (optional) is a type of string
  rapid_commit = null
  # status - (optional) is a type of string
  status = null
  # subnet - (required) is a type of string
  subnet = null
  # upstream_interface - (optional) is a type of string
  upstream_interface = null

  ip_range = [{
    end_ip   = null
    id       = null
    start_ip = null
  }]

  prefix_range = [{
    end_prefix    = null
    id            = null
    prefix_length = null
    start_prefix  = null
  }]
}
```

[top](#index)

### Variables

```terraform
variable "dns_search_list" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "dns_server1" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "dns_server2" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "dns_server3" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "dns_service" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "domain" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "fosid" {
  description = "(required)"
  type        = number
}

variable "interface" {
  description = "(required)"
  type        = string
}

variable "ip_mode" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "lease_time" {
  description = "(optional)"
  type        = number
  default     = null
}

variable "option1" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "option2" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "option3" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "rapid_commit" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "status" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "subnet" {
  description = "(required)"
  type        = string
}

variable "upstream_interface" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "ip_range" {
  description = "nested block: NestingList, min items: 0, max items: 0"
  type = set(object(
    {
      end_ip   = string
      id       = number
      start_ip = string
    }
  ))
  default = []
}

variable "prefix_range" {
  description = "nested block: NestingList, min items: 0, max items: 0"
  type = set(object(
    {
      end_prefix    = string
      id            = number
      prefix_length = number
      start_prefix  = string
    }
  ))
  default = []
}
```

[top](#index)

### Resource

```terraform
resource "fortios_systemdhcp6_server" "this" {
  dns_search_list    = var.dns_search_list
  dns_server1        = var.dns_server1
  dns_server2        = var.dns_server2
  dns_server3        = var.dns_server3
  dns_service        = var.dns_service
  domain             = var.domain
  fosid              = var.fosid
  interface          = var.interface
  ip_mode            = var.ip_mode
  lease_time         = var.lease_time
  option1            = var.option1
  option2            = var.option2
  option3            = var.option3
  rapid_commit       = var.rapid_commit
  status             = var.status
  subnet             = var.subnet
  upstream_interface = var.upstream_interface

  dynamic "ip_range" {
    for_each = var.ip_range
    content {
      end_ip   = ip_range.value["end_ip"]
      id       = ip_range.value["id"]
      start_ip = ip_range.value["start_ip"]
    }
  }

  dynamic "prefix_range" {
    for_each = var.prefix_range
    content {
      end_prefix    = prefix_range.value["end_prefix"]
      id            = prefix_range.value["id"]
      prefix_length = prefix_range.value["prefix_length"]
      start_prefix  = prefix_range.value["start_prefix"]
    }
  }

}
```

[top](#index)

### Outputs

```terraform
output "dns_search_list" {
  description = "returns a string"
  value       = fortios_systemdhcp6_server.this.dns_search_list
}

output "dns_server1" {
  description = "returns a string"
  value       = fortios_systemdhcp6_server.this.dns_server1
}

output "dns_server2" {
  description = "returns a string"
  value       = fortios_systemdhcp6_server.this.dns_server2
}

output "dns_server3" {
  description = "returns a string"
  value       = fortios_systemdhcp6_server.this.dns_server3
}

output "dns_service" {
  description = "returns a string"
  value       = fortios_systemdhcp6_server.this.dns_service
}

output "domain" {
  description = "returns a string"
  value       = fortios_systemdhcp6_server.this.domain
}

output "id" {
  description = "returns a string"
  value       = fortios_systemdhcp6_server.this.id
}

output "ip_mode" {
  description = "returns a string"
  value       = fortios_systemdhcp6_server.this.ip_mode
}

output "lease_time" {
  description = "returns a number"
  value       = fortios_systemdhcp6_server.this.lease_time
}

output "option1" {
  description = "returns a string"
  value       = fortios_systemdhcp6_server.this.option1
}

output "option2" {
  description = "returns a string"
  value       = fortios_systemdhcp6_server.this.option2
}

output "option3" {
  description = "returns a string"
  value       = fortios_systemdhcp6_server.this.option3
}

output "rapid_commit" {
  description = "returns a string"
  value       = fortios_systemdhcp6_server.this.rapid_commit
}

output "status" {
  description = "returns a string"
  value       = fortios_systemdhcp6_server.this.status
}

output "upstream_interface" {
  description = "returns a string"
  value       = fortios_systemdhcp6_server.this.upstream_interface
}

output "this" {
  value = fortios_systemdhcp6_server.this
}
```

[top](#index)