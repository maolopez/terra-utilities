# google_kms_crypto_key_iam_policy

[back](../google.md)

### Index

- [Example Usage](#example-usage)
- [Variables](#variables)
- [Datasource](#datasource)
- [Outputs](#outputs)

### Terraform

```hcl
terraform {
  required_providers {
    google = ">= 3.51.0"
  }
}
```

[top](#index)

### Example Usage

```hcl
module "google_kms_crypto_key_iam_policy" {
  source = "./modules/google/r/google_kms_crypto_key_iam_policy"

  # crypto_key_id - (required) is a type of string
  crypto_key_id = null
  # policy_data - (required) is a type of string
  policy_data = null
}
```

[top](#index)

### Variables

```hcl
variable "crypto_key_id" {
  description = "(required)"
  type        = string
}

variable "policy_data" {
  description = "(required)"
  type        = string
}
```

[top](#index)

### Resource

```hcl
resource "google_kms_crypto_key_iam_policy" "this" {
  crypto_key_id = var.crypto_key_id
  policy_data   = var.policy_data
}
```

[top](#index)

### Outputs

```hcl
output "etag" {
  description = "returns a string"
  value       = google_kms_crypto_key_iam_policy.this.etag
}

output "id" {
  description = "returns a string"
  value       = google_kms_crypto_key_iam_policy.this.id
}

output "this" {
  value = google_kms_crypto_key_iam_policy.this
}
```

[top](#index)