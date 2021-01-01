# aws_acmpca_certificate_authority
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
module "aws_acmpca_certificate_authority" {
  source = "./modules/aws/r/aws_acmpca_certificate_authority"

  # enabled - (optional) is a type of bool
  enabled = null
  # permanent_deletion_time_in_days - (optional) is a type of number
  permanent_deletion_time_in_days = null
  # tags - (optional) is a type of map of string
  tags = {}
  # type - (optional) is a type of string
  type = null

  certificate_authority_configuration = [{
    key_algorithm     = null
    signing_algorithm = null
    subject = [{
      common_name                  = null
      country                      = null
      distinguished_name_qualifier = null
      generation_qualifier         = null
      given_name                   = null
      initials                     = null
      locality                     = null
      organization                 = null
      organizational_unit          = null
      pseudonym                    = null
      state                        = null
      surname                      = null
      title                        = null
    }]
  }]

  revocation_configuration = [{
    crl_configuration = [{
      custom_cname       = null
      enabled            = null
      expiration_in_days = null
      s3_bucket_name     = null
    }]
  }]

  timeouts = [{
    create = null
  }]
}
```
[top](#index)
### Variables
```hcl
variable "enabled" {
  description = "(optional)"
  type        = bool
  default     = null
}

variable "permanent_deletion_time_in_days" {
  description = "(optional)"
  type        = number
  default     = null
}

variable "tags" {
  description = "(optional)"
  type        = map(string)
  default     = null
}

variable "type" {
  description = "(optional)"
  type        = string
  default     = null
}

variable "certificate_authority_configuration" {
  description = "nested mode: NestingList, min items: 1, max items: 1"
  type = set(object(
    {
      key_algorithm     = string
      signing_algorithm = string
      subject = list(object(
        {
          common_name                  = string
          country                      = string
          distinguished_name_qualifier = string
          generation_qualifier         = string
          given_name                   = string
          initials                     = string
          locality                     = string
          organization                 = string
          organizational_unit          = string
          pseudonym                    = string
          state                        = string
          surname                      = string
          title                        = string
        }
      ))
    }
  ))
}

variable "revocation_configuration" {
  description = "nested mode: NestingList, min items: 0, max items: 1"
  type = set(object(
    {
      crl_configuration = list(object(
        {
          custom_cname       = string
          enabled            = bool
          expiration_in_days = number
          s3_bucket_name     = string
        }
      ))
    }
  ))
  default = []
}

variable "timeouts" {
  description = "nested mode: NestingSingle, min items: 0, max items: 0"
  type = set(object(
    {
      create = string
    }
  ))
  default = []
}
```
[top](#index)

### Resource
```hcl
resource "aws_acmpca_certificate_authority" "this" {
  enabled                         = var.enabled
  permanent_deletion_time_in_days = var.permanent_deletion_time_in_days
  tags                            = var.tags
  type                            = var.type

  dynamic "certificate_authority_configuration" {
    for_each = var.certificate_authority_configuration
    content {
      key_algorithm     = certificate_authority_configuration.value["key_algorithm"]
      signing_algorithm = certificate_authority_configuration.value["signing_algorithm"]

      dynamic "subject" {
        for_each = certificate_authority_configuration.value.subject
        content {
          common_name                  = subject.value["common_name"]
          country                      = subject.value["country"]
          distinguished_name_qualifier = subject.value["distinguished_name_qualifier"]
          generation_qualifier         = subject.value["generation_qualifier"]
          given_name                   = subject.value["given_name"]
          initials                     = subject.value["initials"]
          locality                     = subject.value["locality"]
          organization                 = subject.value["organization"]
          organizational_unit          = subject.value["organizational_unit"]
          pseudonym                    = subject.value["pseudonym"]
          state                        = subject.value["state"]
          surname                      = subject.value["surname"]
          title                        = subject.value["title"]
        }
      }

    }
  }

  dynamic "revocation_configuration" {
    for_each = var.revocation_configuration
    content {

      dynamic "crl_configuration" {
        for_each = revocation_configuration.value.crl_configuration
        content {
          custom_cname       = crl_configuration.value["custom_cname"]
          enabled            = crl_configuration.value["enabled"]
          expiration_in_days = crl_configuration.value["expiration_in_days"]
          s3_bucket_name     = crl_configuration.value["s3_bucket_name"]
        }
      }

    }
  }

  dynamic "timeouts" {
    for_each = var.timeouts
    content {
      create = timeouts.value["create"]
    }
  }

}
```
[top](#index)
### Outputs
```hcl
output "arn" {
  description = "returns a string"
  value       = aws_acmpca_certificate_authority.this.arn
}

output "certificate" {
  description = "returns a string"
  value       = aws_acmpca_certificate_authority.this.certificate
}

output "certificate_chain" {
  description = "returns a string"
  value       = aws_acmpca_certificate_authority.this.certificate_chain
}

output "certificate_signing_request" {
  description = "returns a string"
  value       = aws_acmpca_certificate_authority.this.certificate_signing_request
}

output "id" {
  description = "returns a string"
  value       = aws_acmpca_certificate_authority.this.id
}

output "not_after" {
  description = "returns a string"
  value       = aws_acmpca_certificate_authority.this.not_after
}

output "not_before" {
  description = "returns a string"
  value       = aws_acmpca_certificate_authority.this.not_before
}

output "serial" {
  description = "returns a string"
  value       = aws_acmpca_certificate_authority.this.serial
}

output "status" {
  description = "returns a string"
  value       = aws_acmpca_certificate_authority.this.status
}

output "this" {
  value = aws_acmpca_certificate_authority.this
}
```
[top](#index)