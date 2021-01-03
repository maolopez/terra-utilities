# azurerm_virtual_hub

[back](../azurerm.md)

### Index

- [Example Usage](#example-usage)
- [Variables](#variables)
- [Resource](#resource)
- [Outputs](#outputs)

### Terraform

```terraform
terraform {
  required_providers {
    azurerm = ">= 2.41.0"
  }
}
```

[top](#index)

### Example Usage

```terraform
module "azurerm_virtual_hub" {
  source = "./modules/azurerm/r/azurerm_virtual_hub"

  # address_prefix - (optional) is a type of string
  address_prefix = null
  # location - (required) is a type of string
  location = null
  # name - (required) is a type of string
  name = null
  # resource_group_name - (required) is a type of string
  resource_group_name = null
  # sku - (optional) is a type of string
  sku = null
  # tags - (optional) is a type of map of string
  tags = {}
  # virtual_wan_id - (optional) is a type of string
  virtual_wan_id = null

  route = [{
    address_prefixes    = []
    next_hop_ip_address = null
  }]

  timeouts = [{
    create = null
    delete = null
    read   = null
    update = null
  }]
}
```

[top](#index)

### Variables

```terraform
variable "address_prefix" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "location" {
  description = "(required)"
  type        = string
}

variable "name" {
  description = "(required)"
  type        = string
}

variable "resource_group_name" {
  description = "(required)"
  type        = string
}

variable "sku" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "tags" {
  description = "(optional)"
  type        = map(string)
  default     = null
}

variable "virtual_wan_id" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "route" {
  description = "nested block: NestingSet, min items: 0, max items: 0"
  type = set(object(
    {
      address_prefixes    = list(string)
      next_hop_ip_address = string
    }
  ))
  default = []
}

variable "timeouts" {
  description = "nested block: NestingSingle, min items: 0, max items: 0"
  type = set(object(
    {
      create = string
      delete = string
      read   = string
      update = string
    }
  ))
  default = []
}
```

[top](#index)

### Resource

```terraform
resource "azurerm_virtual_hub" "this" {
  address_prefix      = var.address_prefix
  location            = var.location
  name                = var.name
  resource_group_name = var.resource_group_name
  sku                 = var.sku
  tags                = var.tags
  virtual_wan_id      = var.virtual_wan_id

  dynamic "route" {
    for_each = var.route
    content {
      address_prefixes    = route.value["address_prefixes"]
      next_hop_ip_address = route.value["next_hop_ip_address"]
    }
  }

  dynamic "timeouts" {
    for_each = var.timeouts
    content {
      create = timeouts.value["create"]
      delete = timeouts.value["delete"]
      read   = timeouts.value["read"]
      update = timeouts.value["update"]
    }
  }

}
```

[top](#index)

### Outputs

```terraform
output "id" {
  description = "returns a string"
  value       = azurerm_virtual_hub.this.id
}

output "this" {
  value = azurerm_virtual_hub.this
}
```

[top](#index)