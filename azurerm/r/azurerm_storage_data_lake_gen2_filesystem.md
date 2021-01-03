# azurerm_storage_data_lake_gen2_filesystem

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
module "azurerm_storage_data_lake_gen2_filesystem" {
  source = "./modules/azurerm/r/azurerm_storage_data_lake_gen2_filesystem"

  # name - (required) is a type of string
  name = null
  # properties - (optional) is a type of map of string
  properties = {}
  # storage_account_id - (required) is a type of string
  storage_account_id = null

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
variable "name" {
  description = "(required)"
  type        = string
}

variable "properties" {
  description = "(optional)"
  type        = map(string)
  default     = null
}

variable "storage_account_id" {
  description = "(required)"
  type        = string
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
resource "azurerm_storage_data_lake_gen2_filesystem" "this" {
  name               = var.name
  properties         = var.properties
  storage_account_id = var.storage_account_id

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
  value       = azurerm_storage_data_lake_gen2_filesystem.this.id
}

output "this" {
  value = azurerm_storage_data_lake_gen2_filesystem.this
}
```

[top](#index)