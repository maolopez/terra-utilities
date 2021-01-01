# vsphere_datacenter

[back](../vsphere.md)

### Index

- [Example Usage](#example-usage)
- [Variables](#variables)
- [Datasource](#datasource)
- [Outputs](#outputs)

### Terraform

```hcl
terraform {
  required_providers {
    vsphere = ">= 1.24.3"
  }
}
```

[top](#index)

### Example Usage

```hcl
module "vsphere_datacenter" {
  source = "./modules/vsphere/d/vsphere_datacenter"

  # name - (optional) is a type of string
  name = null
}
```

[top](#index)

### Variables

```hcl
variable "name" {
  description = "(optional) - The name of the datacenter. This can be a name or path.\tCan be omitted if there is only one datacenter in your inventory."
  type        = string
  default     = null
}
```

[top](#index)

### Datasource

```hcl
data "vsphere_datacenter" "this" {
  name = var.name
}
```

[top](#index)

### Outputs

```hcl
output "id" {
  description = "returns a string"
  value       = data.vsphere_datacenter.this.id
}

output "this" {
  value = vsphere_datacenter.this
}
```

[top](#index)