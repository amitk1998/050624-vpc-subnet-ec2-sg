# **Azure App Service Module**

Terraform module to create Azure App Service

# **Description**

This module is used to create an Azure App Service. It requires several attributes in order to be created on Azure, including `location`, `resource_group_name`, `service_plan`, `site_config`, etc.

# **Variable Definitions**

| Name | Description | Type | Required | Default | Example |
|------|-------------|------|----------|---------|:-------:|
| <a name="input_location"></a>[location](#input\_location) | Location for web app | `string` | Yes | N/A | `"East US"` |
| <a name="input_resource_group_name"></a>[resource_group_name](#input\_resource_group_name) | Resource group name for web app | `string` | Yes | N/A | `"my-resource-group"` |
| <a name="input_service_plan"></a>[service_plan](#input\_service_plan) | Service plan for web app | `object` | No | `null` | See below |
| <a name="input_windows_web_app_name"></a>[windows_web_app_name](#input\_windows_web_app_name) | Name for windows web app | `string` | No | `null` | `"my-windows-web-app"` |
| <a name="input_linux_web_app_name"></a>[linux_web_app_name](#input\_linux_web_app_name) | Web app slot name for windows | `string` | No | `null` | `"my-linux-web-app"` |
| <a name="input_site_config"></a>[site_config](#input\_site_config) | Site configuration for web app | `object` | No | `null` | See below |
| <a name="input_app_settings"></a>[app_settings](#input\_app_settings) | A map of key-value pairs of App Settings | `map(string)` | No | `null` | `{ setting1 = "value1", setting2 = "value2" }` |
| <a name="input_auth_settings_v1"></a>[auth_settings_v1](#input\_auth_settings_v1) | Authentication settings for App service | `object` | No | `null` | See below |
| <a name="input_auth_settings_v2"></a>[auth_settings_v2](#input\_auth_settings_v2) | Authentication settings for App service v2 | `object` | No | `null` | See below |
| <a name="input_backup"></a>[backup](#input\_backup) | Backup for App Service | `object` | No | `null` | See below |
| <a name="input_client_affinity_enabled"></a>[client_affinity_enabled](#input\_client_affinity_enabled) | Should Client Affinity be enabled? | `bool` | No | `null` | `true` |
| <a name="input_client_certificate_enabled"></a>[client_certificate_enabled](#input\_client_certificate_enabled) | Should Client Certificates be enabled? | `bool` | No | `null` | `true` |
| <a name="input_client_certificate_mode"></a>[client_certificate_mode](#input\_client_certificate_mode) | The Client Certificate mode | `string` | No | `null` | `"Required"` |
| <a name="input_client_certificate_exclusion_paths"></a>[client_certificate_exclusion_paths](#input\_client_certificate_exclusion_paths) | Paths to exclude when using client certificates | `string` | No | `null` | `"path1;path2"` |
| <a name="input_connection_string"></a>[connection_string](#input\_connection_string) | One or more connection strings | `object` | No | `null` | See below |
| <a name="input_enabled"></a>[enabled](#input\_enabled) | Should the Windows Web App be enabled? | `bool` | No | `true` | `false` |
| <a name="input_ftp_publish_basic_authentication_enabled"></a>[ftp_publish_basic_authentication_enabled](#input\_ftp_publish_basic_authentication_enabled) | Should the default FTP basic authentication publishing profile be enabled? | `bool` | No | `true` | `false` |
| <a name="input_https_only"></a>[https_only](#input\_https_only) | Should the Windows Web App require HTTPS connections | `string` | No | `null` | `"Enabled"` |
| <a name="input_public_network_access_enabled"></a>[public_network_access_enabled](#input\_public_network_access_enabled) | Should public network access be enabled for the Web App | `bool` | No | `true` | `false` |
| <a name="input_identity"></a>[identity](#input\_identity) | An identity block | `object` | No | `null` | See below |
| <a name="input_key_vault_reference_identity_id"></a>[key_vault_reference_identity_id](#input\_key_vault_reference_identity_id) | The User Assigned Identity ID used for accessing KeyVault secrets | `string` | No | `null` | `"identity-id"` |
| <a name="input_logs"></a>[logs](#input\_logs) | A logs block | `object` | No | `null` | See below |
| <a name="input_sticky_settings"></a>[sticky_settings](#input\_sticky_settings) | A sticky settings block | `object` | No | `null` | See below |
| <a name="input_storage_account"></a>[storage_account](#input\_storage_account) | One or more storage account blocks | `list(object)` | No | `null` | See below |
| <a name="input_tags"></a>[tags](#input\_tags) | A mapping of tags for the Windows Web App | `map(string)` | No | `null` | `{ environment = "dev" }` |
| <a name="input_virtual_network_subnet_id"></a>[virtual_network_subnet_id](#input\_virtual_network_subnet_id) | The subnet id for regional virtual network integration | `string` | No | `null` | `"subnet-id"` |
| <a name="input_zip_deploy_file"></a>[zip_deploy_file](#input\_zip_deploy_file) | The local path and filename of the Zip packaged application to deploy to this Windows Web App | `string` | No | `null` | `"path/to/app.zip"` |

**Service Plan Example:**

```hcl
service_plan = {
  name                         = "my-service-plan"
  os_type                      = "Windows"
  sku_name                     = "F1"
  app_service_environment_id   = null
  maximum_elastic_worker_count = null
  worker_count                 = null
  per_site_scaling_enabled     = false
  zone_balancing_enabled       = null
}
