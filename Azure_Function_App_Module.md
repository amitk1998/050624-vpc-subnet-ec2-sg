# **Azure Function App Module**

Terraform module to create an Azure Function App.

# **Description**

This module is used to create an Azure Function App. It requires several attributes in order to be created on Azure, including `function_app_name`, `resource_group_name`, `location`, `sku_name`, etc.

# **Variable Definitions**

| Name | Description | Type | Required | Default | Example |
|------|-------------|------|----------|---------|:-------:|
| <a name="input_function_app_name"></a>[function_app_name](#input\_function_app_name) | Name of the Function App. | `string` | Yes | `""` | `"my-function-app"` |
| <a name="input_resource_group_name"></a>[resource_group_name](#input\_resource_group_name) | Name of the Azure Resource Group. | `string` | Yes | `""` | `"my-resource-group"` |
| <a name="input_location"></a>[location](#input\_location) | Azure region where the Function App should be created. | `string` | Yes | `""` | `"East US"` |
| <a name="input_sku_name"></a>[sku_name](#input\_sku_name) | SKU for the Function App plan. | `string` | Yes | `""` | `"Y1"` |
| <a name="input_service_plan_name"></a>[service_plan_name](#input\_service_plan_name) | Name of the service plan. | `string` | Yes | `""` | `"my-service-plan"` |
| <a name="input_app_service_environment_id"></a>[app_service_environment_id](#input\_app_service_environment_id) | ID of the Service Environment. | `string` | No | `null` | `"service-environment-id"` |
| <a name="input_maximum_elastic_worker_count"></a>[maximum_elastic_worker_count](#input\_maximum_elastic_worker_count) | Maximum number of workers to be used in the plan. | `number` | No | `null` | `10` |
| <a name="input_worker_count"></a>[worker_count](#input\_worker_count) | Number of workers to be allocated. | `number` | No | `null` | `5` |
| <a name="input_per_site_scaling_enabled"></a>[per_site_scaling_enabled](#input\_per_site_scaling_enabled) | Per site scaling enabled. | `bool` | No | `false` | `true` |
| <a name="input_zone_balancing_enabled"></a>[zone_balancing_enabled](#input\_zone_balancing_enabled) | Service Plan balance across Availability Zones in the region. | `bool` | No | `null` | `true` |
| <a name="input_os_type"></a>[os_type](#input\_os_type) | OS type for the Function App (Windows/Linux). | `string` | No | `"Windows"` | `"Linux"` |
| <a name="input_primary_access_key"></a>[primary_access_key](#input\_primary_access_key) | Storage account primary access key. | `string` | No | `null` | `"primary-access-key"` |
| <a name="input_storage_account_name"></a>[storage_account_name](#input\_storage_account_name) | Storage account Name. | `string` | No | `null` | `"storage-account-name"` |
| <a name="input_storage_uses_managed_identity"></a>[storage_uses_managed_identity](#input\_storage_uses_managed_identity) | Set to true if storage uses managed identity, false otherwise. | `bool` | No | `null` | `true` |
| <a name="input_function_app_version"></a>[function_app_version](#input\_function_app_version) | Version of the Function App extension. | `number` | No | `4` | `3` |
| <a name="input_function_app_vnet_integration_subnet_id"></a>[function_app_vnet_integration_subnet_id](#input\_function_app_vnet_integration_subnet_id) | ID of the subnet for VNet integration. | `string` | No | `null` | `"subnet-id"` |
| <a name="input_function_app_application_settings"></a>[function_app_application_settings](#input\_function_app_application_settings) | Application settings for the Function App. | `map(string)` | No | `null` | `{ setting1 = "value1", setting2 = "value2" }` |
| <a name="input_win_site_config"></a>[win_site_config](#input\_win_site_config) | Site Configuration for Windows OS. | `object({})` | No | `{}` | See below |
| <a name="input_lin_site_config"></a>[lin_site_config](#input\_lin_site_config) | Site Configuration for Linux OS. | `object({})` | No | `{}` | See below |
| <a name="input_sticky_settings"></a>[sticky_settings](#input\_sticky_settings) | Settings for sticky connections. | `list(object({}))` | No | `null` | See below |
| <a name="input_https_only"></a>[https_only](#input\_https_only) | Enable HTTPS-only access. | `bool` | No | `null` | `true` |
| <a name="input_client_certificate_enabled"></a>[client_certificate_enabled](#input\_client_certificate_enabled) | Enable client certificate. | `bool` | No | `null` | `true` |
| <a name="input_client_certificate_mode"></a>[client_certificate_mode](#input\_client_certificate_mode) | Client certificate mode. | `string` | No | `null` | `"Require"` |
| <a name="input_builtin_logging_enabled"></a>[builtin_logging_enabled](#input\_builtin_logging_enabled) | Enable built-in logging. | `bool` | No | `null` | `true` |
| <a name="input_identity_type"></a>[identity_type](#input\_identity_type) | Type of identity. | `string` | No | `null` | `"SystemAssigned"` |
| <a name="input_identity_ids"></a>[identity_ids](#input\_identity_ids) | User-assigned identity IDs. | `list(string)` | No | `null` | `["identity-id1", "identity-id2"]` |
| <a name="input_connection_string"></a>[connection_string](#input\_connection_string) | Connection string settings. | `list(object({}))` | No | `null` | See below |
| <a name="input_tags"></a>[tags](#input\_tags) | Tags for the Azure Function App. | `map(string)` | No | `{}` | `{ environment = "dev" }` |

## **Example Usage**

```hcl
module "function_app" {
  source                            = "tfe.axisb.com/ax-tfe/function-app/azurerm"
  version                           = "X.X.X"
  function_app_name                = "my-function-app"
  resource_group_name              = "my-resource-group"
  location                         = "East US"
  sku_name                         = "Y1"
  service_plan_name                = "my-service-plan"
  maximum_elastic_worker_count     = 10
  worker_count                     = 5
  per_site_scaling_enabled         = true
  zone_balancing_enabled           = true
  os_type                          = "Windows"
  primary_access_key               = "primary-access-key"
  storage_account_name             = "storage-account-name"
  storage_uses_managed_identity    = true
  function_app_version             = 3
  function_app_vnet_integration_subnet_id = "subnet-id"
  function_app_application_settings = {
    setting1 = "value1"
    setting2 = "value2"
  }
  win_site_config = {
    always_on                              = true
    http2_enabled                          = true
    load_balancing_mode                    = "WeightedRoundRobin"
    minimum_tls_version                    = "1.2"
    remote_debugging_enabled               = true
    remote_debugging_version               = "VS2019"
    websockets_enabled                     = true
    application_insights_connection_string = "connection-string"
    application_insights_key               = true
    pre_warmed_instance_count              = 2
    worker_count                           = 3
  }
  https_only                      = true
  client_certificate_enabled      = true
  client_certificate_mode         = "Require"
  builtin_logging_enabled         = true
  identity_type                   = "SystemAssigned"
  identity_ids                    = ["identity-id1", "identity-id2"]
  connection_string               = [
    {
      name  = "conn1"
      type  = "SQL"
      value = "connection-string1"
    },
    {
      name  = "conn2"
      type  = "NoSQL"
      value = "connection-string2"
    }
  ]
  tags                             = { environment = "dev" }
}
