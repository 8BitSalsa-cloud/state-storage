# state storage

This S3 bucket, stores different terraform states.
It is versioned, has no public access, is decrypted by KMS, is protected to destroy and is locked so that you can work as a team.

## setup


In the config file the state file needs a unique name

```
bucket = "jens-tf-state-storage"  
key    = "state-storage/terraform.tfstate" <-- change here
region = "eu-central-1"
dynamodb_table = "jens-tf-state-lock"  <-- change here
kms_key_id = "tf-state-storage"
```

To set up a new terrafom state in the state bucket you have inital terraform with the backend configuration.

```
terraform init -backend-config=backend.config
```

## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_aws"></a> [aws](#requirement\_aws) | ~> 4.0 |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_aws"></a> [aws](#provider\_aws) | 4.64.0 |

## Modules

No modules.

## Resources

| Name | Type |
|------|------|
| [aws_dynamodb_table.this](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/dynamodb_table) | resource |
| [aws_kms_alias.this](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/kms_alias) | resource |
| [aws_kms_key.this](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/kms_key) | resource |
| [aws_s3_bucket.this](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/s3_bucket) | resource |
| [aws_s3_bucket_policy.this](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/s3_bucket_policy) | resource |
| [aws_s3_bucket_public_access_block.this](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/s3_bucket_public_access_block) | resource |
| [aws_s3_bucket_server_side_encryption_configuration.this](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/s3_bucket_server_side_encryption_configuration) | resource |
| [aws_s3_bucket_versioning.this](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/s3_bucket_versioning) | resource |
| [aws_caller_identity.current](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/caller_identity) | data source |
| [aws_iam_policy_document.bucket_policy](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/iam_policy_document) | data source |
| [aws_iam_policy_document.key_policy](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/iam_policy_document) | data source |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| <a name="input_aws_kms_alias"></a> [aws\_kms\_alias](#input\_aws\_kms\_alias) | Alias of the KMS key used for the state storage. | `string` | n/a | yes |
| <a name="input_aws_region"></a> [aws\_region](#input\_aws\_region) | aws\_region terraform will deploy the code. | `string` | n/a | yes |
| <a name="input_tf_state_storage_bucket_name"></a> [tf\_state\_storage\_bucket\_name](#input\_tf\_state\_storage\_bucket\_name) | Name of the state storage bucket. | `string` | n/a | yes |
| <a name="input_tf_state_storage_dynamodb_lock_name"></a> [tf\_state\_storage\_dynamodb\_lock\_name](#input\_tf\_state\_storage\_dynamodb\_lock\_name) | Name of the dynamoDB table to lock the terraform state. | `string` | n/a | yes |

## Outputs

No outputs.
