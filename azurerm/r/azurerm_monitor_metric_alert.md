# azurerm_monitor_metric_alert

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
module "azurerm_monitor_metric_alert" {
  source = "./modules/azurerm/r/azurerm_monitor_metric_alert"

  # auto_mitigate - (optional) is a type of bool
  auto_mitigate = null
  # description - (optional) is a type of string
  description = null
  # enabled - (optional) is a type of bool
  enabled = null
  # frequency - (optional) is a type of string
  frequency = null
  # name - (required) is a type of string
  name = null
  # resource_group_name - (required) is a type of string
  resource_group_name = null
  # scopes - (required) is a type of set of string
  scopes = []
  # severity - (optional) is a type of number
  severity = null
  # tags - (optional) is a type of map of string
  tags = {}
  # target_resource_location - (optional) is a type of string
  target_resource_location = null
  # target_resource_type - (optional) is a type of string
  target_resource_type = null
  # window_size - (optional) is a type of string
  window_size = null

  action = [{
    action_group_id    = null
    webhook_properties = {}
  }]

  application_insights_web_test_location_availability_criteria = [{
    component_id          = null
    failed_location_count = null
    web_test_id           = null
  }]

  criteria = [{
    aggregation = null
    dimension = [{
      name     = null
      operator = null
      values   = []
    }]
    metric_name      = null
    metric_namespace = null
    operator         = null
    threshold        = null
  }]

  dynamic_criteria = [{
    aggregation       = null
    alert_sensitivity = null
    dimension = [{
      name     = null
      operator = null
      values   = []
    }]
    evaluation_failure_count = null
    evaluation_total_count   = null
    ignore_data_before       = null
    metric_name              = null
    metric_namespace         = null
    operator                 = null
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
variable "auto_mitigate" {
  description = "(optional)"
  type        = bool
  default     = null
}

variable "description" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "enabled" {
  description = "(optional)"
  type        = bool
  default     = null
}

variable "frequency" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "name" {
  description = "(required)"
  type        = string
}

variable "resource_group_name" {
  description = "(required)"
  type        = string
}

variable "scopes" {
  description = "(required)"
  type        = set(string)
}

variable "severity" {
  description = "(optional)"
  type        = number
  default     = null
}

variable "tags" {
  description = "(optional)"
  type        = map(string)
  default     = null
}

variable "target_resource_location" {
  description = "(optional) - The location of the target resource. Required when using subscription, resource group scope or multiple scopes."
  type        = string
  default     = null
}

variable "target_resource_type" {
  description = "(optional) - The resource type (e.g. Microsoft.Compute/virtualMachines) of the target resource. Required when using subscription, resource group scope or multiple scopes."
  type        = string
  default     = null
}

variable "window_size" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "action" {
  description = "nested block: NestingSet, min items: 0, max items: 0"
  type = set(object(
    {
      action_group_id    = string
      webhook_properties = map(string)
    }
  ))
  default = []
}

variable "application_insights_web_test_location_availability_criteria" {
  description = "nested block: NestingList, min items: 0, max items: 1"
  type = set(object(
    {
      component_id          = string
      failed_location_count = number
      web_test_id           = string
    }
  ))
  default = []
}

variable "criteria" {
  description = "nested block: NestingSet, min items: 0, max items: 0"
  type = set(object(
    {
      aggregation = string
      dimension = list(object(
        {
          name     = string
          operator = string
          values   = list(string)
        }
      ))
      metric_name      = string
      metric_namespace = string
      operator         = string
      threshold        = number
    }
  ))
  default = []
}

variable "dynamic_criteria" {
  description = "nested block: NestingSet, min items: 0, max items: 1"
  type = set(object(
    {
      aggregation       = string
      alert_sensitivity = string
      dimension = list(object(
        {
          name     = string
          operator = string
          values   = list(string)
        }
      ))
      evaluation_failure_count = number
      evaluation_total_count   = number
      ignore_data_before       = string
      metric_name              = string
      metric_namespace         = string
      operator                 = string
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
resource "azurerm_monitor_metric_alert" "this" {
  auto_mitigate            = var.auto_mitigate
  description              = var.description
  enabled                  = var.enabled
  frequency                = var.frequency
  name                     = var.name
  resource_group_name      = var.resource_group_name
  scopes                   = var.scopes
  severity                 = var.severity
  tags                     = var.tags
  target_resource_location = var.target_resource_location
  target_resource_type     = var.target_resource_type
  window_size              = var.window_size

  dynamic "action" {
    for_each = var.action
    content {
      action_group_id    = action.value["action_group_id"]
      webhook_properties = action.value["webhook_properties"]
    }
  }

  dynamic "application_insights_web_test_location_availability_criteria" {
    for_each = var.application_insights_web_test_location_availability_criteria
    content {
      component_id          = application_insights_web_test_location_availability_criteria.value["component_id"]
      failed_location_count = application_insights_web_test_location_availability_criteria.value["failed_location_count"]
      web_test_id           = application_insights_web_test_location_availability_criteria.value["web_test_id"]
    }
  }

  dynamic "criteria" {
    for_each = var.criteria
    content {
      aggregation      = criteria.value["aggregation"]
      metric_name      = criteria.value["metric_name"]
      metric_namespace = criteria.value["metric_namespace"]
      operator         = criteria.value["operator"]
      threshold        = criteria.value["threshold"]

      dynamic "dimension" {
        for_each = criteria.value.dimension
        content {
          name     = dimension.value["name"]
          operator = dimension.value["operator"]
          values   = dimension.value["values"]
        }
      }

    }
  }

  dynamic "dynamic_criteria" {
    for_each = var.dynamic_criteria
    content {
      aggregation              = dynamic_criteria.value["aggregation"]
      alert_sensitivity        = dynamic_criteria.value["alert_sensitivity"]
      evaluation_failure_count = dynamic_criteria.value["evaluation_failure_count"]
      evaluation_total_count   = dynamic_criteria.value["evaluation_total_count"]
      ignore_data_before       = dynamic_criteria.value["ignore_data_before"]
      metric_name              = dynamic_criteria.value["metric_name"]
      metric_namespace         = dynamic_criteria.value["metric_namespace"]
      operator                 = dynamic_criteria.value["operator"]

      dynamic "dimension" {
        for_each = dynamic_criteria.value.dimension
        content {
          name     = dimension.value["name"]
          operator = dimension.value["operator"]
          values   = dimension.value["values"]
        }
      }

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
  value       = azurerm_monitor_metric_alert.this.id
}

output "target_resource_location" {
  description = "returns a string"
  value       = azurerm_monitor_metric_alert.this.target_resource_location
}

output "target_resource_type" {
  description = "returns a string"
  value       = azurerm_monitor_metric_alert.this.target_resource_type
}

output "this" {
  value = azurerm_monitor_metric_alert.this
}
```

[top](#index)