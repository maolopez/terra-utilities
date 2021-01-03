# fortios_firewall_address6

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
module "fortios_firewall_address6" {
  source = "./modules/fortios/r/fortios_firewall_address6"

  # cache_ttl - (optional) is a type of number
  cache_ttl = null
  # color - (optional) is a type of number
  color = null
  # comment - (optional) is a type of string
  comment = null
  # end_ip - (optional) is a type of string
  end_ip = null
  # fqdn - (optional) is a type of string
  fqdn = null
  # host - (optional) is a type of string
  host = null
  # host_type - (optional) is a type of string
  host_type = null
  # ip6 - (optional) is a type of string
  ip6 = null
  # name - (optional) is a type of string
  name = null
  # obj_id - (optional) is a type of string
  obj_id = null
  # sdn - (optional) is a type of string
  sdn = null
  # start_ip - (optional) is a type of string
  start_ip = null
  # template - (optional) is a type of string
  template = null
  # type - (optional) is a type of string
  type = null
  # uuid - (optional) is a type of string
  uuid = null
  # visibility - (optional) is a type of string
  visibility = null

  list = [{
    ip = null
  }]

  subnet_segment = [{
    name  = null
    type  = null
    value = null
  }]

  tagging = [{
    category = null
    name     = null
    tags = [{
      name = null
    }]
  }]
}
```

[top](#index)

### Variables

```terraform
variable "cache_ttl" {
  description = "(optional)"
  type        = number
  default     = null
}

variable "color" {
  description = "(optional)"
  type        = number
  default     = null
}

variable "comment" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "end_ip" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "fqdn" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "host" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "host_type" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "ip6" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "name" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "obj_id" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "sdn" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "start_ip" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "template" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "type" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "uuid" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "visibility" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "list" {
  description = "nested block: NestingList, min items: 0, max items: 0"
  type = set(object(
    {
      ip = string
    }
  ))
  default = []
}

variable "subnet_segment" {
  description = "nested block: NestingList, min items: 0, max items: 0"
  type = set(object(
    {
      name  = string
      type  = string
      value = string
    }
  ))
  default = []
}

variable "tagging" {
  description = "nested block: NestingList, min items: 0, max items: 0"
  type = set(object(
    {
      category = string
      name     = string
      tags = list(object(
        {
          name = string
        }
      ))
    }
  ))
  default = []
}
```

[top](#index)

### Resource

```terraform
resource "fortios_firewall_address6" "this" {
  cache_ttl  = var.cache_ttl
  color      = var.color
  comment    = var.comment
  end_ip     = var.end_ip
  fqdn       = var.fqdn
  host       = var.host
  host_type  = var.host_type
  ip6        = var.ip6
  name       = var.name
  obj_id     = var.obj_id
  sdn        = var.sdn
  start_ip   = var.start_ip
  template   = var.template
  type       = var.type
  uuid       = var.uuid
  visibility = var.visibility

  dynamic "list" {
    for_each = var.list
    content {
      ip = list.value["ip"]
    }
  }

  dynamic "subnet_segment" {
    for_each = var.subnet_segment
    content {
      name  = subnet_segment.value["name"]
      type  = subnet_segment.value["type"]
      value = subnet_segment.value["value"]
    }
  }

  dynamic "tagging" {
    for_each = var.tagging
    content {
      category = tagging.value["category"]
      name     = tagging.value["name"]

      dynamic "tags" {
        for_each = tagging.value.tags
        content {
          name = tags.value["name"]
        }
      }

    }
  }

}
```

[top](#index)

### Outputs

```terraform
output "cache_ttl" {
  description = "returns a number"
  value       = fortios_firewall_address6.this.cache_ttl
}

output "color" {
  description = "returns a number"
  value       = fortios_firewall_address6.this.color
}

output "end_ip" {
  description = "returns a string"
  value       = fortios_firewall_address6.this.end_ip
}

output "fqdn" {
  description = "returns a string"
  value       = fortios_firewall_address6.this.fqdn
}

output "host" {
  description = "returns a string"
  value       = fortios_firewall_address6.this.host
}

output "host_type" {
  description = "returns a string"
  value       = fortios_firewall_address6.this.host_type
}

output "id" {
  description = "returns a string"
  value       = fortios_firewall_address6.this.id
}

output "ip6" {
  description = "returns a string"
  value       = fortios_firewall_address6.this.ip6
}

output "name" {
  description = "returns a string"
  value       = fortios_firewall_address6.this.name
}

output "sdn" {
  description = "returns a string"
  value       = fortios_firewall_address6.this.sdn
}

output "start_ip" {
  description = "returns a string"
  value       = fortios_firewall_address6.this.start_ip
}

output "template" {
  description = "returns a string"
  value       = fortios_firewall_address6.this.template
}

output "type" {
  description = "returns a string"
  value       = fortios_firewall_address6.this.type
}

output "uuid" {
  description = "returns a string"
  value       = fortios_firewall_address6.this.uuid
}

output "visibility" {
  description = "returns a string"
  value       = fortios_firewall_address6.this.visibility
}

output "this" {
  value = fortios_firewall_address6.this
}
```

[top](#index)