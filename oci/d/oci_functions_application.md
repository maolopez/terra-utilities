# oci_functions_application

[back](../oci.md)

### Index

- [Example Usage](#example-usage)
- [Variables](#variables)
- [Datasource](#datasource)
- [Outputs](#outputs)

### Terraform

```terraform
terraform {
  required_providers {
    oci = ">= 4.7.0"
  }
}
```

[top](#index)

### Example Usage

```terraform
module "oci_functions_application" {
  source = "./modules/oci/d/oci_functions_application"

  # application_id - (required) is a type of string
  application_id = null
}
```

[top](#index)

### Variables

```terraform
variable "application_id" {
  description = "(required)"
  type        = string
}
```

[top](#index)

### Datasource

```terraform
data "oci_functions_application" "this" {
  application_id = var.application_id
}
```

[top](#index)

### Outputs

```terraform
output "compartment_id" {
  description = "returns a string"
  value       = data.oci_functions_application.this.compartment_id
}

output "config" {
  description = "returns a map of string"
  value       = data.oci_functions_application.this.config
}

output "defined_tags" {
  description = "returns a map of string"
  value       = data.oci_functions_application.this.defined_tags
}

output "display_name" {
  description = "returns a string"
  value       = data.oci_functions_application.this.display_name
}

output "freeform_tags" {
  description = "returns a map of string"
  value       = data.oci_functions_application.this.freeform_tags
}

output "id" {
  description = "returns a string"
  value       = data.oci_functions_application.this.id
}

output "state" {
  description = "returns a string"
  value       = data.oci_functions_application.this.state
}

output "subnet_ids" {
  description = "returns a list of string"
  value       = data.oci_functions_application.this.subnet_ids
}

output "syslog_url" {
  description = "returns a string"
  value       = data.oci_functions_application.this.syslog_url
}

output "time_created" {
  description = "returns a string"
  value       = data.oci_functions_application.this.time_created
}

output "time_updated" {
  description = "returns a string"
  value       = data.oci_functions_application.this.time_updated
}

output "this" {
  value = oci_functions_application.this
}
```

[top](#index)