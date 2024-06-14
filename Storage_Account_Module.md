# **Azure Storage Account Module**
 
Terraform module to create Azure Storage Account
 
# **Description**
 
This module is used to create an Azure Storage Account. It requires several attributes in order to be created on Azure, including `name`, `resource_group_name`, `location`, `account_kind`, etc.
 
# **Variable Definitions**
 
| Name | Description | Type | Required | Default | Example |
|------|-------------|------|----------|---------|:-------:|
| <a name="input_existing_storage_account_name"></a>[existing_storage_account_name](#input\_existing\_storage\_account\_name) | Name of the existing storage account | `string` | No | `null` | `"existing-storage-account"` |
| <a name="input_log_analytics_workspace_id"></a>[log_analytics_workspace_id](#input\_log\_analytics\_workspace\_id) | Id of log analytic workspace | `string` | No | `null` | `"log-analytics-id"` |
| <a name="input_eventhub_name"></a>[eventhub_name](#input\_eventhub\_name) | The name of eventhub-name | `string` | No | `null` | `"eventhub-name"` |
| <a name="input_existing_storage_resource_group_name"></a>[existing_storage_resource_group_name](#input\_existing\_storage\_resource\_group\_name) | Name of the existing storage account's resource group | `string` | No | `null` | `"existing-resource-group"` |
| <a name="input_name"></a>[name](#input\_name) | The name of the storage account. | `string` | Yes | `""` | `"mystorageaccount"` |
| <a name="input_resource_group_name"></a>[resource_group_name](#input\_resource\_group\_name) | The name of the resource group in which to create the storage account. | `string` | Yes | `""` | `"my-resource-group"` |
| <a name="input_location"></a>[location](#input\_location) | The Azure region in which the storage account should be created. | `string` | Yes | `""` | `"East US"` |
| <a name="input_account_kind"></a>[account_kind](#input\_account\_kind) | Defines the Kind of account. | `string` | No | `"StorageV2"` | `"Storage"` |
| <a name="input_account_tier"></a>[account_tier](#input\_account\_tier) | The tier of the storage account. | `string` | No | `null` | `"Standard"` |
| <a name="input_enable_storage_account_defender"></a>[enable_storage_account_defender](#input\_enable\_storage\_account\_defender) | Whether to enable storage account defender or not. | `bool` | No | `false` | `true` |
| <a name="input_account_replication_type"></a>[account_replication_type](#input\_account\_replication\_type) | The replication type of the storage account. | `string` | No | `null` | `"LRS"` |
| <a name="input_cross_tenant_replication_enabled"></a>[cross_tenant_replication_enabled](#input\_cross\_tenant\_replication\_enabled) | Indicates whether cross-tenant replication is enabled. | `bool` | No | `true` | `false` |
| <a name="input_access_tier"></a>[access_tier](#input\_access\_tier) | The access tier of the storage account. | `string` | No | `"Hot"` | `"Cool"` |
| <a name="input_edge_zone"></a>[edge_zone](#input\_edge\_zone) | The edge zone for the storage account. | `string` | No | `null` | `"edge-zone"` |
| <a name="input_enable_https_traffic_only"></a>[enable_https_traffic_only](#input\_enable\_https\_traffic\_only) | Indicates whether to enable HTTPS traffic only. | `bool` | No | `true` | `false` |
| <a name="input_min_tls_version"></a>[min_tls_version](#input\_min\_tls\_version) | The minimum TLS version required for the storage account. | `string` | No | `"TLS1_2"` | `"TLS1_0"` |
| <a name="input_allow_nested_items_to_be_public"></a>[allow_nested_items_to_be_public](#input\_allow\_nested\_items\_to\_be\_public) | Indicates whether nested items can be public. | `bool` | No | `true` | `false` |
| <a name="input_shared_access_key_enabled"></a>[shared_access_key_enabled](#input\_shared\_access\_key\_enabled) | Indicates whether shared access keys are enabled. | `bool` | No | `true` | `false` |
| <a name="input_shared_access_key_reminder"></a>[shared_access_key_reminder](#input\_shared\_access\_key\_reminder) | Shared access key reminder. | `string` | No | `null` | `"Reminder message"` |
| <a name="input_public_network_access_enabled"></a>[public_network_access_enabled](#input\_public\_network\_access\_enabled) | Indicates whether public network access is enabled. | `bool` | No | `false` | `true` |
| <a name="input_default_to_oauth_authentication"></a>[default_to_oauth_authentication](#input\_default\_to\_oauth\_authentication) | Indicates whether to default to OAuth authentication. | `bool` | No | `false` | `true` |
| <a name="input_is_hns_enabled"></a>[is_hns_enabled](#input\_is\_hns\_enabled) | Indicates whether hierarchical namespace is enabled. | `bool` | No | `null` | `true` |
| <a name="input_sftp_enabled"></a>[sftp_enabled](#input\_sftp\_enabled) | Boolean flag to enable or disable SFTP. | `bool` | No | `false` | `true` |
| <a name="input_nfsv3_enabled"></a>[nfsv3_enabled](#input\_nfsv3\_enabled) | Boolean flag to enable or disable NFSv3. | `bool` | No | `false` | `true` |
| <a name="input_tags"></a>[tags](#input\_tags) | A map of tags to apply to the storage account. | `map(string)` | No | `{}` | `{ environment = "dev" }` |
| <a name="input_managed_identity_type"></a>[managed_identity_type](#input\_managed\_identity\_type) | The type of managed identity for the storage account. | `string` | No | `null` | `"SystemAssigned"` |
| <a name="input_managed_identity_ids"></a>[managed_identity_ids](#input\_managed\_identity\_ids) | The IDs of user-assigned managed identities. | `list(string)` | No | `null` | `["managed-identity-id"]` |
| <a name="input_blob_soft_delete_retention_days"></a>[blob_soft_delete_retention_days](#input\_blob\_soft\_delete\_retention\_days) | The number of days that blobs should be retained for soft delete. | `number` | No | `null` | `30` |
| <a name="input_container_soft_delete_retention_days"></a>[container_soft_delete_retention_days](#input\_container\_soft\_delete\_retention\_days) | The number of days that containers should be retained for soft delete. | `number` | No | `null` | `30` |
| <a name="input_enable_versioning"></a>[enable_versioning](#input\_enable\_versioning) | Indicates whether blob versioning is enabled. | `bool` | No | `null` | `true` |
| <a name="input_last_access_time_enabled"></a>[last_access_time_enabled](#input\_last\_access\_time\_enabled) | Indicates whether last access time tracking is enabled. | `bool` | No | `null` | `true` |
| <a name="input_change_feed_enabled"></a>[change_feed_enabled](#input\_change\_feed\_enabled) | Indicates whether change feed is enabled. | `bool` | No | `null` | `true` |
| <a name="input_network_rules"></a>[network_rules](#input\_network\_rules) | Network rules configuration for the storage account. | `object({ default_action = string bypass = optional(list(string)) ip_rules = optional(list(string)) subnet_ids = optional(list(string)) private_link_access =optional(list(object({ endpoint_resource_id = string endpoint_tenant_id = optional(string) })),[]) })` | No | `null` | `{ default_action = "Allow" }` |
| <a name="input_custom_domain"></a>[custom_domain](#input\_custom\_domain) | Custom domain configuration for the storage account. | `object({ name = string use_subdomain = optional(bool) })` | No | `null` | `{ name = "custom-domain" }` |
| <a name="input_customer_managed_key"></a>[customer_managed_key](#input\_customer\_managed\_key) | Customer managed key configuration for the storage account. | `object({ key_vault_key_id = string user_assigned_identity_id = string })` | No | `null` | `{ key_vault_key_id = "key-vault-key-id" }` |
| <a name="input_existing_storage_container_name"></a>[existing_storage_container_name](#input\_existing\_storage\_container\_name) | The name of an existing storage container. | `string` | No | `null` | `"existing-container-name"` |
| <a name="input_container_name"></a>[container_name](#input\_container\_name) | The name of the storage container to create. | `string` | No | `null` | `"my-container"` |
| <a name="input_containers_access_type"></a>[containers_access_type](#input\_containers\_access\_type) | The access type for the storage container. | `string` | No | `null` | `"private"` |
| <a name="input_create_storage_container"></a>[create_storage_container](#input\_create\_storage\_container) | Indicates whether to create Azure Storage container. | `bool` | No | `false` | `true` |
| <a name="input_create_storage_blob"></a>[create_storage_blob](#input\_create\_storage\_blob) | Indicates whether to create Azure Storage Blobs. | `bool` | No | `false` | `true` |
| <a name="input_blob_name"></a>[blob_name](#input\_blob\_name) | The name of the blob. | `string` | No | `null` | `"my-blob"` |
| <a name="input_blob_type"></a>[blob_type](#input\_blob\_type) | The type of blob. | `string` | No | `null` | `"Block"` |
| <a name="input_size"></a>[size](#input\_size) | The size of the blob. | `number` | No | `null` | `1024` |
| <a name="input_content_type"></a>[content_type](#input\_content\_type) | The content type of the blob. | `string` | No | `""` | `"application/json"` |
| <a name="input_content_md5"></a>[content_md5](#input\_content\_md5) | The MD5 hash of the blob's content. | `string` | No | `null` | `"MD5-hash"` |
| <a name="input_metadata"></a>[metadata](#input\_metadata) | A map of metadata to associate with the blob. | `map(string)` | No | `null` | `{ key1 = "value1", key2 = "value2" }` |
| <a name="input_queues"></a>[queues](#input\_queues) | A list of storage queue names. | `list(string)` | No | `[]` | `["queue1", "queue2"]` |
| <a name="input_enable_advanced_threat_protection"></a>[enable_advanced_threat_protection](#input\_enable\_advanced\_threat\_protection) | Indicates whether advanced threat protection is enabled for the storage account. | `bool` | No | `null` | `true` |
| <a name="input_module_source"></a>[module_source](#input\_module\_source) | Source for the storage blob | `string` | No | `""` | `"tfe.axisb.com/ax-tfe/storage-account/azurerm"` |
| <a name="input_blob_cors"></a>[blob_cors](#input\_blob\_cors) | blob service cors rules. | `map(object({ allowed_headers = list(string) allowed_methods = list(string) allowed_origins = list(string) exposed_headers = list(string) max_age_in_seconds = number }))` | No | `null` | `{ cors_rule = [{ allowed_headers = ["*"] allowed_methods = ["PUT", "GET"] allowed_origins = ["*"] exposed_headers = ["*"] max_age_in_seconds = 3600 }] }` |
| <a name="input_storage_share"></a>[storage_share](#input\_storage\_share) | Share properties for storage account. | `map(object({ access_tier = optional(string) enabled_protocol = optional(string) metadata = optional(map(string)) name = string quota = number acl = optional(list(object({ id = string access_policy = optional(list(object({ expiry = optional(string) permissions = string start = optional(string) }))) }))) }))` | No | `{}` | `{ share1 = { name = "my-share" quota = 10 } }` |
| <a name="input_storage_table"></a>[storage_table](#input\_storage\_table) | Table properties for storage account. | `map(object({ name = string acl = optional(list(object({ id = string access_policy = optional(list(object({ expiry = string permissions = string start = string }))) }))) }))` | No | `{}` | `{ table1 = { name = "my-table" } }` |
| <a name="input_azure_file_authentication"></a>[azure_file_authentication](#input\_azure\_file\_authentication) | Azure file authentication block. | `list(object({ directory_type = string active_directory = optional(list(object({ domain_name = string domain_guide = string domain_sid = optional(string) storage_sid = optional(string) forest_name = optional(string) netbios_domain_name = optional(string) }))) }))` | No | `null` | `[ { directory_type = "Microsoft.ActiveDirectory" } ]` |
| <a name="input_routing"></a>[routing](#input\_routing) | Routing block for Storage account. | `list(object({ publish_internet_endpoints = optional(bool) publish_microsoft_endpoints = optional(bool) choice = optional(string) }))` | No | `null` | `[ { choice = "InternetRouting" } ]` |
| <a name="input_static_website"></a>[static_website](#input\_static\_website) | Static website block for Storage account. | `list(object({ index_document = optional(string) error_404_document = optional(string) }))` | No | `null` | `[ { index_document = "index.html" } ]` |
| <a name="input_use_customer_managed_key"></a>[use_customer_managed_key](#input\_use\_customer\_managed\_key) | Flag to create customer_managed_key | `bool` | No | `true` | `false` |
| <a name="input_create_policy"></a>[create_policy](#input\_create\_policy) | Flag to create policy | `bool` | No | `true` | `false` |
| <a name="input_key_vault_id"></a>[key_vault_id](#input\_key\_vault\_id) | ID of the key vault. | `string` | No | `null` | `"key-vault-id"` |
| <a name="input_key_name"></a>[key_name](#input\_key\_name) | Name of the key vault key. | `string` | No | `null` | `"key-name"` |
| <a name="input_key_version"></a>[key_version](#input\_key\_version) | Version of the key vault key. | `string` | No | `null` | `"key-version"` |
| <a name="input_user_assigned_identity_id"></a>[user_assigned_identity_id](#input\_user\_assigned\_identity\_id) | ID of the user assigned identity. | `string` | No | `null` | `"identity-id"` |
| <a name="input_federated_identity_client_id"></a>[federated_identity_client_id](#input\_federated\_identity\_client\_id) | ID of the federated client. | `string` | No | `null` | `"federated-id"` |
| <a name="input_tenant_id"></a>[tenant_id](#input\_tenant\_id) | ID of the tenant. | `string` | No | `null` | `"tenant-id"` |
| <a name="input_key_permissions"></a>[key_permissions](#input\_key\_permissions) | Key permissions for the storage account. | `list(string)` | No | `["Get", "WrapKey", "UnwrapKey"]` | `["Get", "WrapKey"]` |
| <a name="input_secret_permissions"></a>[secret_permissions](#input\_secret\_permissions) | Secret permissions for the storage account. | `list(string)` | No | `["Get"]` | `["Get", "Set"]` |
| <a name="input_certificate_permissions"></a>[certificate_permissions](#input\_certificate\_permissions) | Certificate permissions for the storage account. | `list(string)` | No | `null` | `["Get", "List"]` |
| <a name="input_storage_permissions"></a>[storage_permissions](#input\_storage\_permissions) | Storage permissions for the storage account. | `list(string)` | No | `null` | `["Get", "List", "Delete"]` |
| <a name="input_storage_account_que_properties"></a>[storage_account_que_properties](#input\_storage\_account\_que\_properties) | Queue properties for storage account. | `object({ cors_rule = optional(list(object({ allowed_headers = list(string) allowed_methods = list(string) allowed_origins = list(string) exposed_headers = list(string) max_age_in_seconds = number })) hour_metrics = optional(object({ enabled = bool version = optional(bool) include_apis = optional(number) retention_policy_days = string })) logging = optional(object({ delete = bool read = bool version = string write = optional(bool) retention_policy_days = optional(number) })) minute_metrics = optional(object({ enabled = bool version = string include_apis = optional(bool) retention_policy_days = string })) })` | No | `null` | `{}` |
| <a name="input_storage_account_share_properties"></a>[storage_account_share_properties](#input\_storage\_account\_share\_properties) | Share properties for storage account. | `object({ cors_rule = optional(list(object({ allowed_headers = list(string) allowed_methods = list(string) allowed_origins = list(string) exposed_headers = list(string) max_age_in_seconds = number })) retention_policy = optional(object({ days = optional(number) })) smb = optional(object({ authentication_types = optional(set(string)) channel_encryption_type = optional(set(string)) kerberos_ticket_encryption_type = optional(set(string)) multichannel_enabled = optional(bool) versions = optional(set(string)) })) })` | No | `null` | `{}` |
| <a name="input_private_endpoint_subnet_id"></a>[private_endpoint_subnet_id](#input\_private\_endpoint\_subnet\_id) | Private Endpoint Subnet Id. | `string` | Yes |  | `"subnet-id"` |
| <a name="input_private_dns_zone_group"></a>[private_dns_zone_group](#input\_private\_dns\_zone\_group) | Private DNS Zone Group details. | `list(object({ name = optional(string) private_dns_zone_ids = list(string) }))` | No |  | `[{ name = "my-zone-group", private_dns_zone_ids = ["zone-id1", "zone-id2"] }]` |
| <a name="input_is_manual_connection"></a>[is_manual_connection](#input\_is\_manual\_connection) | Set Manual Connection. | `bool` | No | `false` | `true` |
| <a name="input_private_endpoint_subresource_names"></a>[private_endpoint_subresource_names](#input\_private\_endpoint\_subresource\_names) | Subresource Names for Private Endpoint. | `list(string)` | No |  | `["blob", "file"]` |
| <a name="input_enable_logicapp_storageaccount_privateendpoint"></a>[enable_logicapp_storageaccount_privateendpoint](#input\_enable\_logicapp\_storageaccount\_privateendpoint) | Whether to enable private endpoint for logicapp or not. | `bool` | No | `false` | `true` |


## Example Usage

```hcl
module "storage_account" {
  source                              = "tfe.axisb.com/ax-tfe/storage-account/azurerm"
  version                             = "X.X.X"
  name                                = "storage-account-name"
  resource_group_name                 = "my-resource-group"
  location                            = "East US"
  account_kind                        = "StorageV2"
  account_tier                        = "Standard"
  enable_storage_account_defender     = true
  account_replication_type            = "LRS"
  cross_tenant_replication_enabled    = true
  access_tier                         = "Hot"
  edge_zone                           = "edge-zone"
  enable_https_traffic_only           = true
  min_tls_version                     = "TLS1_2"
  allow_nested_items_to_be_public     = true
  shared_access_key_enabled           = true
  shared_access_key_reminder          = "key-reminder"
  public_network_access_enabled       = false
  default_to_oauth_authentication    = false
  is_hns_enabled                      = true
  sftp_enabled                        = true
  nfsv3_enabled                       = true
  tags                                = { environment = "dev" }
  managed_identity_type               = "UserAssigned"
  managed_identity_ids                = ["identity-id"]
  blob_soft_delete_retention_days     = 7
  container_soft_delete_retention_days = 7
  enable_versioning                   = true
  last_access_time_enabled            = true
  change_feed_enabled                 = true
  network_rules = {
    default_action     = "Allow"
    bypass             = ["AzureServices"]
    ip_rules           = ["10.0.0.0/24"]
    subnet_ids         = ["subnet-id1", "subnet-id2"]
    private_link_access = [{
      endpoint_resource_id = "resource-id"
      endpoint_tenant_id   = "tenant-id"
    }]
  }
  custom_domain = {
    name          = "www.example.com"
    use_subdomain = true
  }
  customer_managed_key = {
    key_vault_key_id          = "key-vault-key-id"
    user_assigned_identity_id = "identity-id"
  }
  existing_storage_container_name = "existing-container-name"
  container_name                  = "my-container"
  containers_access_type          = "private"
  create_storage_container        = true
  create_storage_blob             = true
  blob_name                       = "my-blob"
  blob_type                       = "Block"
  size                            = 1024
  content_type                    = "application/json"
  content_md5                     = "MD5-hash"
  metadata                        = { key1 = "value1", key2 = "value2" }
  queues                          = ["queue1", "queue2"]
  enable_advanced_threat_protection = true
  module_source                   = "tfe.axisb.com/ax-tfe/storage-account/azurerm"
  blob_cors = {
    cors_rule = [{
      allowed_headers    = ["*"]
      allowed_methods    = ["PUT", "GET"]
      allowed_origins    = ["*"]
      exposed_headers    = ["*"]
      max_age_in_seconds = 3600
    }]
  }
  storage_share = {
    share1 = {
      name  = "my-share"
      quota = 10
    }
  }
  storage_table = {
    table1 = {
      name = "my-table"
    }
  }
  azure_file_authentication = [{
    directory_type = "Microsoft.ActiveDirectory"
  }]
  routing = [{
    choice = "InternetRouting"
  }]
  static_website = [{
    index_document     = "index.html"
    error_404_document = "error.html"
  }]
  use_customer_managed_key     = true
  create_policy                = true
  key_vault_id                = "key-vault-id"
  key_name                     = "key-name"
  key_version                  = "key-version"
  user_assigned_identity_id   = "identity-id"
  federated_identity_client_id = "federated-id"
  tenant_id                   = "tenant-id"
  key_permissions             = ["Get", "WrapKey"]
  secret_permissions          = ["Get", "Set"]
  certificate_permissions     = ["Get", "List"]
  storage_permissions         = ["Get", "List", "Delete"]
  storage_account_que_properties = {
    cors_rule = [{
      allowed_headers    = ["*"]
      allowed_methods    = ["PUT", "GET"]
      allowed_origins    = ["*"]
      exposed_headers    = ["*"]
      max_age_in_seconds = 3600
    }]
    hour_metrics = {
      enabled                    = true
      version                    = true
      include_apis               = 0
      retention_policy_days      = "2"
    }
    logging = {
      delete                 = true
      read                   = true
      version                = "1.0"
      write                  = true
      retention_policy_days = 2
    }
    minute_metrics = {
      enabled                    = true
      version                    = "1.0"
      include_apis               = 0
      retention_policy_days      = "1"
    }
  }
  storage_account_share_properties = {
    cors_rule = [{
      allowed_headers    = ["*"]
      allowed_methods    = ["PUT", "GET"]
      allowed_origins    = ["*"]
      exposed_headers    = ["*"]
      max_age_in_seconds = 3600
    }]
    retention_policy = {
      days = 1
    }
    smb = {
      authentication_types       = ["Kerberos"]
      channel_encryption_type    = ["AES-128-GCM"]
      kerberos_ticket_encryption_type = ["AES-128-GCM"]
      multichannel_enabled       = true
      versions                   = ["2.0"]
    }
  }
  private_endpoint_subnet_id = "subnet-id"
  private_dns_zone_group     = [{
    name                = "my-zone-group"
    private_dns_zone_ids = ["zone-id1", "zone-id2"]
  }]
  is_manual_connection                   = true
  private_endpoint_subresource_names     = ["blob", "file"]
  enable_logicapp_storageaccount_privateendpoint = true
}
