# **Azure Data Factory Module**

Terraform module to create Azure Data Factory.

## **Description**

This module is used to create an Azure Data Factory. It requires several attributes in order to be created on Azure, including `name`, `resource_group_name`, `location`, `github_configuration`, `global_parameter`, `identity`, `vsts_configuration`, `managed_virtual_network_enabled`, `public_network_enabled`, `customer_managed_key_id`, `customer_managed_key_identity_id`, `purview_id`, `tags`, `integration_runtime_type`, `runtime_name`, `azure_runtime_configuration`, `node_size`, `ssis_runtime_configuration`, `catalog_info`, `custom_setup_script`, `express_custom_setup`, `express_vnet_integration`, `package_store`, `proxy`, `vnet_integration`, `self_hosted_runtime_description`, and `rbac_authorization`.

## **Variable Definitions**

| Name | Description | Type | Required | Default | Example |
|------|-------------|------|----------|---------|:-------:|
| <a name="input_name"></a>[name](#input\_name) | Name of the Azure Data Factory. | `string` | Yes | `""` | `"my-data-factory"` |
| <a name="input_resource_group_name"></a>[resource_group_name](#input\_resource_group_name) | Name of the Azure resource group. | `string` | Yes | `""` | `"my-resource-group"` |
| <a name="input_location"></a>[location](#input\_location) | Azure region where the Azure Data Factory will be deployed. | `string` | Yes | `""` | `"East US"` |
| <a name="input_github_configuration"></a>[github_configuration](#input\_github_configuration) | Github configuration of the Azure Data Factory. | `object` | No | `null` | `{ account_name = "github-account", branch_name = "main", git_url = "https://github.com/example.git", repository_name = "repo", root_folder = "root" }` |
| <a name="input_global_parameter"></a>[global_parameter](#input\_global_parameter) | Global parameter of the Azure Data Factory. | `object` | No | `null` | `{ name = "param", type = "string", value = "value" }` |
| <a name="input_identity"></a>[identity](#input\_identity) | Identity of the Azure Data Factory. | `object` | No | `null` | `{ type = "SystemAssigned", identity_ids = ["id1", "id2"] }` |
| <a name="input_vsts_configuration"></a>[vsts_configuration](#input\_vsts_configuration) | VSTS configuration of the Azure Data Factory. | `object` | No | `null` | `{ account_name = "vsts-account", branch_name = "main", project_name = "project", repository_name = "repo", root_folder = "root", tenant_id = "tenant-id" }` |
| <a name="input_managed_virtual_network_enabled"></a>[managed_virtual_network_enabled](#input\_managed_virtual_network_enabled) | Managed virtual network enabled of the Azure Data Factory. | `bool` | No | `null` | `true` |
| <a name="input_public_network_enabled"></a>[public_network_enabled](#input\_public_network_enabled) | Public network enabled of the Azure Data Factory. | `bool` | No | `true` | `false` |
| <a name="input_customer_managed_key_id"></a>[customer_managed_key_id](#input\_customer_managed_key_id) | Customer managed key id of the Azure Data Factory. | `string` | No | `null` | `"key-id"` |
| <a name="input_customer_managed_key_identity_id"></a>[customer_managed_key_identity_id](#input\_customer_managed_key_identity_id) | Customer managed key identity id of the Azure Data Factory. | `string` | No | `null` | `"identity-id"` |
| <a name="input_purview_id"></a>[purview_id](#input\_purview_id) | Purview id of the Azure Data Factory. | `string` | No | `null` | `"purview-id"` |
| <a name="input_tags"></a>[tags](#input\_tags) | Tags of the Azure Data Factory. | `map(string)` | No | `{}` | `{ environment = "dev" }` |
| <a name="input_integration_runtime_type"></a>[integration_runtime_type](#input\_integration_runtime_type) | Integration runtime type of the Azure Data Factory. Possible values Azure, AzureSSIS or SelfHosted. | `string` | No | `null` | `"Azure"` |
| <a name="input_runtime_name"></a>[runtime_name](#input\_runtime_name) | Name of the integration runtime. | `string` | No | `null` | `"my-integration-runtime"` |
| <a name="input_azure_runtime_configuration"></a>[azure_runtime_configuration](#input\_azure_runtime_configuration) | Azure integration runtime configuration. | `object` | No | `null` | `{ description = "runtime", cleanup_enabled = true, compute_type = "type", core_count = 4, time_to_live_min = 60, virtual_network_enabled = true }` |
| <a name="input_node_size"></a>[node_size](#input\_node_size) | Node size of the SSIS integration runtime. Required if integration runtime type is AzureSSIS. | `string` | No | `null` | `"Standard_D4s_v3"` |
| <a name="input_ssis_runtime_configuration"></a>[ssis_runtime_configuration](#input\_ssis_runtime_configuration) | SSIS integration runtime configuration. | `object` | No | `null` | `{ number_of_nodes = 3, max_parallel_executions_per_node = 4, edition = "Enterprise", license_type = "BYOL", description = "SSIS runtime" }` |
| <a name="input_catalog_info"></a>[catalog_info](#input\_catalog_info) | Catalog info of the SSIS integration runtime. | `object` | No | `null` | `{ server_endpoint = "server", administrator_login = "admin", administrator_password = "password", pricing_tier = "tier", elastic_pool_name = "pool", dual_standby_pair_name = "pair" }` |
| <a name="input_custom_setup_script"></a>[custom_setup_script](#input\_custom_setup_script) | Custom setup script of the SSIS integration runtime. | `object` | No | `null` | `{ blob_container_uri = "uri", sas_token = "token" }` |
| <a name="input_express_custom_setup"></a>[express_custom_setup](#input\_express_custom_setup) | Express custom setup of the SSIS integration runtime. | `object` | No | `null` | `{ command_key = [{ target_name = "target", user_name = "user" }], component = [{ name = "comp", license = "lic" }], environment = "env", powershell_version = "7" }` |
| <a name="input_express_vnet_integration"></a>[express_vnet_integration](#input\_express_vnet_integration) | Express vnet integration of the SSIS integration runtime. | `object` | No | `null` | `{ subnet_id = "subnet-id" }` |
| <a name="input_package_store"></a>[package_store](#input\_package_store) | Package store of the SSIS integration runtime. | `object` | No | `null` | `{ name = "store", linked_service_name = "service" }` |
| <a name="input_proxy"></a>[proxy](#input\_proxy) | Proxy of the SSIS integration runtime. | `object` | No | `null` | `{ self_hosted_integration_runtime_name = "runtime", staging_storage_linked_service_name = "service", path = "path" }` |
| <a name="input_vnet_integration"></a>[vnet_integration](#input\_vnet_integration) | Vnet integration of the SSIS integration runtime. | `object` | No | `null` | `{ vnet_id = "vnet-id", subnet_name = "subnet", subnet_id = "subnet-id", public_ips = ["ip1", "ip2"] }` |
| <a name="input_self_hosted_runtime_description"></a>[self_hosted_runtime_description](#input\_self_hosted_runtime_description) | Self-hosted integration runtime description. | `string` | No | `null` | `"self-hosted-runtime"` |
| <a name="input_rbac_authorization"></a>[rbac_authorization](#input\_rbac_authorization) | Rbac authorization of the self-hosted integration runtime. | `object` | No | `null` | `{ resource_id = "resource-id" }` |

## **Example Usage**

```hcl
module "data_factory" {
  source                         = "tfe.axisb.com/ax-tfe/data-factory/azurerm"
  version                        = "X.X.X"
  name                           = "my-data-factory"
  resource_group_name            = "my-resource-group"
  location                       = "East US"
  github_configuration           = { account_name = "github-account", branch_name = "main", git_url = "https://github.com/example.git", repository_name = "repo", root_folder = "root" }
  global_parameter               = { name = "param", type = "string", value = "value" }
  identity                       = { type = "SystemAssigned", identity_ids = ["id1", "id2"] }
  vsts_configuration             = { account_name = "vsts-account", branch_name = "main", project_name = "project", repository_name = "repo", root_folder = "root", tenant_id = "tenant-id" }
  managed_virtual_network_enabled = true
  public_network_enabled         = false
  customer_managed_key_id         = "key-id"
  customer_managed_key_identity_id = "identity-id"
  purview_id                     = "purview-id"
  tags                           = { environment = "dev" }
  integration_runtime_type       = "Azure"
  runtime_name                   = "my-integration-runtime"
  azure_runtime_configuration   = { description = "runtime", cleanup_enabled = true, compute_type = "type", core_count = 4, time_to_live_min = 60, virtual_network_enabled = true }
  node_size                      = "Standard_D4s_v3"
  ssis_runtime_configuration     = { number_of_nodes = 3, max_parallel_executions_per_node = 4, edition = "Enterprise", license_type = "BYOL", description = "SSIS runtime" }
  catalog_info                   = { server_endpoint = "server", administrator_login = "admin", administrator_password = "password", pricing_tier = "tier", elastic_pool_name = "pool", dual_standby_pair_name = "pair" }
  custom_setup_script            = { blob_container_uri = "uri", sas_token = "token" }
  express_custom_setup           = { command_key = [{ target_name = "target", user_name = "user" }], component = [{ name = "comp", license = "lic" }], environment = "env", powershell_version = "7" }
  express_vnet_integration       = { subnet_id = "subnet-id" }
  package_store                  = { name = "store", linked_service_name = "service" }
  proxy                          = { self_hosted_integration_runtime_name = "runtime", staging_storage_linked_service_name = "service", path = "path" }
  vnet_integration               = { vnet_id = "vnet-id", subnet_name = "subnet", subnet_id = "subnet-id", public_ips = ["ip1", "ip2"] }
  self_hosted_runtime_description = "self-hosted-runtime"
  rbac_authorization             = { resource_id = "resource-id" }
}
