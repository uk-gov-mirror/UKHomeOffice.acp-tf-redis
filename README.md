# acp-tf-redis
Terraform module to build redis elasticache clusters

## Module Usage

```
module "fake_redis" {
  source = "git::https://github.com/UKHomeOffice/acp-tf-redis?ref=v0.0.1"

  name                       = "fake-redis"
  environment                = "${var.environment}"
  node_type                  = "cache.t2.small"
  number_of_nodes            = 2
  cidr_blocks                = "${values(var.compute_cidrs)}"
  subnet_ids                 = ["${var.subnet_ids}"]
  vpc_id                     = "${var.vpc_id}"
}
```

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|:----:|:-----:|:-----:|
| at\_rest\_encryption\_enabled | Should at rest encrption be enabled for this cluster | string | `false` | no |
| auth\_required | Should redis AUTH be enabled for this cluster | string | `false` | no |
| auth\_token | The password for redis AUTH | string | `` | no |
| auto\_minor\_version\_upgrade | Should the cluster autmoatically be updated to the latest minor vesrion | string | `false` | no |
| cidr\_blocks | cidr blocks from which this cluster should accept connections | list | `<list>` | no |
| engine\_version | The engine version for this cluster | string | `4.0.10` | no |
| environment | The environment the redis cluster is running in i.e. dev, prod etc | string | - | yes |
| name | A descriptive name for the redis cluster | string | - | yes |
| node\_type | The type of nodes to use for this cluster | string | - | yes |
| number\_of\_nodes | The number of nodes in this cluster | string | `1` | no |
| paramter\_group\_name | The parameter group name for this cluster | string | `default.redis4.0` | no |
| subnet\_ids | The list of subnet IDs associated to a vpc | list | `<list>` | no |
| tags | A map of tags to add to all resources | map | `<map>` | no |
| transit\_encryption\_enabled | Should transit encryption be enabled for this cluster | string | `false` | no |
| vpc\_id | The VPC ID to create the resources within | string | - | yes |

<!-- BEGIN_TF_DOCS -->
## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) | >= 0.12 |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_aws"></a> [aws](#provider\_aws) | n/a |

## Modules

No modules.

## Resources

| Name | Type |
|------|------|
| [aws_elasticache_replication_group.elasticache_redis_cluster](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/elasticache_replication_group) | resource |
| [aws_elasticache_replication_group.elasticache_redis_cluster_with_auth](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/elasticache_replication_group) | resource |
| [aws_elasticache_subnet_group.elasticache_redis_cluster](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/elasticache_subnet_group) | resource |
| [aws_security_group.elasticache_redis_cluster](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/security_group) | resource |
| [aws_security_group_rule.in_redis_port](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/security_group_rule) | resource |
| [aws_security_group_rule.out_all](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/security_group_rule) | resource |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| <a name="input_at_rest_encryption_enabled"></a> [at\_rest\_encryption\_enabled](#input\_at\_rest\_encryption\_enabled) | Should at rest encrption be enabled for this cluster | `bool` | `false` | no |
| <a name="input_auth_required"></a> [auth\_required](#input\_auth\_required) | Should redis AUTH be enabled for this cluster | `bool` | `false` | no |
| <a name="input_auth_token"></a> [auth\_token](#input\_auth\_token) | The password for redis AUTH | `string` | `""` | no |
| <a name="input_auto_minor_version_upgrade"></a> [auto\_minor\_version\_upgrade](#input\_auto\_minor\_version\_upgrade) | Should the cluster autmoatically be updated to the latest minor vesrion | `bool` | `false` | no |
| <a name="input_cidr_blocks"></a> [cidr\_blocks](#input\_cidr\_blocks) | cidr blocks from which this cluster should accept connections | `list` | `[]` | no |
| <a name="input_engine_version"></a> [engine\_version](#input\_engine\_version) | The engine version for this cluster | `string` | `"4.0.10"` | no |
| <a name="input_environment"></a> [environment](#input\_environment) | The environment the redis cluster is running in i.e. dev, prod etc | `any` | n/a | yes |
| <a name="input_name"></a> [name](#input\_name) | A descriptive name for the redis cluster | `any` | n/a | yes |
| <a name="input_node_type"></a> [node\_type](#input\_node\_type) | The type of nodes to use for this cluster | `any` | n/a | yes |
| <a name="input_number_of_nodes"></a> [number\_of\_nodes](#input\_number\_of\_nodes) | The number of nodes in this cluster | `number` | `1` | no |
| <a name="input_paramter_group_name"></a> [paramter\_group\_name](#input\_paramter\_group\_name) | The parameter group name for this cluster | `string` | `"default.redis4.0"` | no |
| <a name="input_snapshot_retention_limit"></a> [snapshot\_retention\_limit](#input\_snapshot\_retention\_limit) | Redis only: the retention period of snapshots kept in days | `string` | `""` | no |
| <a name="input_snapshot_window"></a> [snapshot\_window](#input\_snapshot\_window) | The daily time range which ElastiCache will begin taking daily snapshots | `string` | `""` | no |
| <a name="input_subnet_ids"></a> [subnet\_ids](#input\_subnet\_ids) | The list of subnet IDs associated to a vpc | `list` | `[]` | no |
| <a name="input_tags"></a> [tags](#input\_tags) | A map of tags to add to all resources | `map` | `{}` | no |
| <a name="input_transit_encryption_enabled"></a> [transit\_encryption\_enabled](#input\_transit\_encryption\_enabled) | Should transit encryption be enabled for this cluster | `bool` | `false` | no |
| <a name="input_vpc_id"></a> [vpc\_id](#input\_vpc\_id) | The VPC ID to create the resources within | `any` | n/a | yes |

## Outputs

No outputs.
<!-- END_TF_DOCS -->