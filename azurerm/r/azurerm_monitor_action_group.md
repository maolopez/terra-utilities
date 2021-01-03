# azurerm_monitor_action_group

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
module "azurerm_monitor_action_group" {
  source = "./modules/azurerm/r/azurerm_monitor_action_group"

  # enabled - (optional) is a type of bool
  enabled = null
  # name - (required) is a type of string
  name = null
  # resource_group_name - (required) is a type of string
  resource_group_name = null
  # short_name - (required) is a type of string
  short_name = null
  # tags - (optional) is a type of map of string
  tags = {}

  arm_role_receiver = [{
    name                    = null
    role_id                 = null
    use_common_alert_schema = null
  }]

  automation_runbook_receiver = [{
    automation_account_id   = null
    is_global_runbook       = null
    name                    = null
    runbook_name            = null
    service_uri             = null
    use_common_alert_schema = null
    webhook_resource_id     = null
  }]

  azure_app_push_receiver = [{
    email_address = null
    name          = null
  }]

  azure_function_receiver = [{
    function_app_resource_id = null
    function_name            = null
    http_trigger_url         = null
    name                     = null
    use_common_alert_schema  = null
  }]

  email_receiver = [{
    email_address           = null
    name                    = null
    use_common_alert_schema = null
  }]

  itsm_receiver = [{
    connection_id        = null
    name                 = null
    region               = null
    ticket_configuration = null
    workspace_id         = null
  }]

  logic_app_receiver = [{
    callback_url            = null
    name                    = null
    resource_id             = null
    use_common_alert_schema = null
  }]

  sms_receiver = [{
    country_code = null
    name         = null
    phone_number = null
  }]

  timeouts = [{
    create = null
    delete = null
    read   = null
    update = null
  }]

  voice_receiver = [{
    country_code = null
    name         = null
    phone_number = null
  }]

  webhook_receiver = [{
    name                    = null
    service_uri             = null
    use_common_alert_schema = null
  }]
}
```

[top](#index)

### Variables

```terraform
variable "enabled" {
  description = "(optional)"
  type        = bool
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

variable "short_name" {
  description = "(required)"
  type        = string
}

variable "tags" {
  description = "(optional)"
  type        = map(string)
  default     = null
}

variable "arm_role_receiver" {
  description = "nested block: NestingList, min items: 0, max items: 0"
  type = set(object(
    {
      name                    = string
      role_id                 = string
      use_common_alert_schema = bool
    }
  ))
  default = []
}

variable "automation_runbook_receiver" {
  description = "nested block: NestingList, min items: 0, max items: 0"
  type = set(object(
    {
      automation_account_id   = string
      is_global_runbook       = bool
      name                    = string
      runbook_name            = string
      service_uri             = string
      use_common_alert_schema = bool
      webhook_resource_id     = string
    }
  ))
  default = []
}

variable "azure_app_push_receiver" {
  description = "nested block: NestingList, min items: 0, max items: 0"
  type = set(object(
    {
      email_address = string
      name          = string
    }
  ))
  default = []
}

variable "azure_function_receiver" {
  description = "nested block: NestingList, min items: 0, max items: 0"
  type = set(object(
    {
      function_app_resource_id = string
      function_name            = string
      http_trigger_url         = string
      name                     = string
      use_common_alert_schema  = bool
    }
  ))
  default = []
}

variable "email_receiver" {
  description = "nested block: NestingList, min items: 0, max items: 0"
  type = set(object(
    {
      email_address           = string
      name                    = string
      use_common_alert_schema = bool
    }
  ))
  default = []
}

variable "itsm_receiver" {
  description = "nested block: NestingList, min items: 0, max items: 0"
  type = set(object(
    {
      connection_id        = string
      name                 = string
      region               = string
      ticket_configuration = string
      workspace_id         = string
    }
  ))
  default = []
}

variable "logic_app_receiver" {
  description = "nested block: NestingList, min items: 0, max items: 0"
  type = set(object(
    {
      callback_url            = string
      name                    = string
      resource_id             = string
      use_common_alert_schema = bool
    }
  ))
  default = []
}

variable "sms_receiver" {
  description = "nested block: NestingList, min items: 0, max items: 0"
  type = set(object(
    {
      country_code = string
      name         = string
      phone_number = string
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

variable "voice_receiver" {
  description = "nested block: NestingList, min items: 0, max items: 0"
  type = set(object(
    {
      country_code = string
      name         = string
      phone_number = string
    }
  ))
  default = []
}

variable "webhook_receiver" {
  description = "nested block: NestingList, min items: 0, max items: 0"
  type = set(object(
    {
      name                    = string
      service_uri             = string
      use_common_alert_schema = bool
    }
  ))
  default = []
}
```

[top](#index)

### Resource

```terraform
resource "azurerm_monitor_action_group" "this" {
  enabled             = var.enabled
  name                = var.name
  resource_group_name = var.resource_group_name
  short_name          = var.short_name
  tags                = var.tags

  dynamic "arm_role_receiver" {
    for_each = var.arm_role_receiver
    content {
      name                    = arm_role_receiver.value["name"]
      role_id                 = arm_role_receiver.value["role_id"]
      use_common_alert_schema = arm_role_receiver.value["use_common_alert_schema"]
    }
  }

  dynamic "automation_runbook_receiver" {
    for_each = var.automation_runbook_receiver
    content {
      automation_account_id   = automation_runbook_receiver.value["automation_account_id"]
      is_global_runbook       = automation_runbook_receiver.value["is_global_runbook"]
      name                    = automation_runbook_receiver.value["name"]
      runbook_name            = automation_runbook_receiver.value["runbook_name"]
      service_uri             = automation_runbook_receiver.value["service_uri"]
      use_common_alert_schema = automation_runbook_receiver.value["use_common_alert_schema"]
      webhook_resource_id     = automation_runbook_receiver.value["webhook_resource_id"]
    }
  }

  dynamic "azure_app_push_receiver" {
    for_each = var.azure_app_push_receiver
    content {
      email_address = azure_app_push_receiver.value["email_address"]
      name          = azure_app_push_receiver.value["name"]
    }
  }

  dynamic "azure_function_receiver" {
    for_each = var.azure_function_receiver
    content {
      function_app_resource_id = azure_function_receiver.value["function_app_resource_id"]
      function_name            = azure_function_receiver.value["function_name"]
      http_trigger_url         = azure_function_receiver.value["http_trigger_url"]
      name                     = azure_function_receiver.value["name"]
      use_common_alert_schema  = azure_function_receiver.value["use_common_alert_schema"]
    }
  }

  dynamic "email_receiver" {
    for_each = var.email_receiver
    content {
      email_address           = email_receiver.value["email_address"]
      name                    = email_receiver.value["name"]
      use_common_alert_schema = email_receiver.value["use_common_alert_schema"]
    }
  }

  dynamic "itsm_receiver" {
    for_each = var.itsm_receiver
    content {
      connection_id        = itsm_receiver.value["connection_id"]
      name                 = itsm_receiver.value["name"]
      region               = itsm_receiver.value["region"]
      ticket_configuration = itsm_receiver.value["ticket_configuration"]
      workspace_id         = itsm_receiver.value["workspace_id"]
    }
  }

  dynamic "logic_app_receiver" {
    for_each = var.logic_app_receiver
    content {
      callback_url            = logic_app_receiver.value["callback_url"]
      name                    = logic_app_receiver.value["name"]
      resource_id             = logic_app_receiver.value["resource_id"]
      use_common_alert_schema = logic_app_receiver.value["use_common_alert_schema"]
    }
  }

  dynamic "sms_receiver" {
    for_each = var.sms_receiver
    content {
      country_code = sms_receiver.value["country_code"]
      name         = sms_receiver.value["name"]
      phone_number = sms_receiver.value["phone_number"]
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

  dynamic "voice_receiver" {
    for_each = var.voice_receiver
    content {
      country_code = voice_receiver.value["country_code"]
      name         = voice_receiver.value["name"]
      phone_number = voice_receiver.value["phone_number"]
    }
  }

  dynamic "webhook_receiver" {
    for_each = var.webhook_receiver
    content {
      name                    = webhook_receiver.value["name"]
      service_uri             = webhook_receiver.value["service_uri"]
      use_common_alert_schema = webhook_receiver.value["use_common_alert_schema"]
    }
  }

}
```

[top](#index)

### Outputs

```terraform
output "id" {
  description = "returns a string"
  value       = azurerm_monitor_action_group.this.id
}

output "this" {
  value = azurerm_monitor_action_group.this
}
```

[top](#index)