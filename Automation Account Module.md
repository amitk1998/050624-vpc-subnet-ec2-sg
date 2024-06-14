## **Automation Account Module**

Terraform module to create an Automation Account in Azure.

### **Description**

This module provisions an Automation Account in Azure with the specified configurations.

### **Variables**

| Name | Description | Type | Required | Default | Example |
|------|-------------|------|----------|---------|:-------:|
| <a name="input_automation_account_name"></a>[automation_account_name](#input\_automation_account_name) | Name of the Automation Account. | `string` | Yes | `""` | `"my-automation-account"` |
| <a name="input_location"></a>[location](#input\_location) | Location for the Automation Account. | `string` | Yes | `""` | `"East US"` |
| <a name="input_resource_group_name"></a>[resource_group_name](#input\_resource_group_name) | Name of the resource group. | `string` | Yes | `""` | `"my-resource-group"` |
| <a name="input_sku_name"></a>[sku_name](#input\_sku_name) | Name of the SKU for the Automation Account. Possible values are Basic and Free. | `string` | Yes | `""` | `"Basic"` |
| <a name="input_local_authentication_enabled"></a>[local_authentication_enabled](#input\_local_authentication_enabled) | Enable local authentication for the Automation Account. | `bool` | No | `true` | `true` |
| <a name="input_public_network_access_enabled"></a>[public_network_access_enabled](#input\_public_network_access_enabled) | Enable public network access for the Automation Account. | `bool` | No | `true` | `true` |
| <a name="input_encryption"></a>[encryption](#input\_encryption) | Encryption settings for the Automation Account. | `object` | No | `null` | `{ key_vault_key_id = "vault-key-id", user_assigned_identity_id = "identity-id" }` |
| <a name="input_identity"></a>[identity](#input\_identity) | Identity settings for the Automation Account. | `object` | No | `null` | `{ type = "SystemAssigned", identity_ids = ["identity-id"] }` |
| <a name="input_tags"></a>[tags](#input\_tags) | Tags for the Automation Account. | `map(string)` | No | `{}` | `{ environment = "dev" }` |
| <a name="input_log_analytics_workspace_name"></a>[log_analytics_workspace_name](#input\_log_analytics_workspace_name) | Name of Log Analytics Workspace (optional). | `string` | No | `null` | `"my-log-analytics-workspace"` |
| <a name="input_hub_storage_account_name"></a>[hub_storage_account_name](#input\_hub_storage_account_name) | Name of Hub Storage Account (optional). | `string` | No | `null` | `"my-hub-storage-account"` |
| <a name="input_storage_account_id"></a>[storage_account_id](#input\_storage_account_id) | Storage Account ID for Diagnostic Setting. | `string` | No | `null` | `"storage-account-id"` |
| <a name="input_log_analytics_workspace_id"></a>[log_analytics_workspace_id](#input\_log_analytics_workspace_id) | Log Analytics Workspace ID for Diagnostic Setting. | `string` | No | `null` | `"log-analytics-workspace-id"` |
| <a name="input_auto_diag_logs"></a>[auto_diag_logs](#input\_auto_diag_logs) | List of logs to enable for diagnostics. | `list(string)` | No | `[]` | `["ApplicationLogs", "SecurityLogs"]` |
| <a name="input_private_endpoint_subnet_id"></a>[private_endpoint_subnet_id](#input\_private_endpoint_subnet_id) | Private Endpoint Subnet Id. | `string` | No | `null` | `"subnet-id"` |
| <a name="input_private_dns_zone_group"></a>[private_dns_zone_group](#input\_private_dns_zone_group) | Private DNS Zone Group details. | `list(object)` | No | `[]` | `[{ name = "zone-group-name", private_dns_zone_ids = ["private-dns-zone-id1", "private-dns-zone-id2"] }]` |
| <a name="input_is_manual_connection"></a>[is_manual_connection](#input\_is_manual_connection) | Set Manual Connection. | `bool` | No | `false` | `true` |

### **Example Usage**

```hcl
module "automation_account" {
  source                        = "tfe.axisb.com/ax-tfe/automation-account/azurerm"
  version                       = "X.X.X"
  automation_account_name       = "my-automation-account"
  location                      = "East US"
  resource_group_name           = "my-resource-group"
  sku_name                      = "Basic"
  local_authentication_enabled  = true
  public_network_access_enabled = true
  encryption                    = {
    key_vault_key_id         = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/my-resource-group/providers/Microsoft.KeyVault/vaults/my-key-vault/keys/my-key"
    user_assigned_identity_id = null
  }
  identity                      = {
    type         = "SystemAssigned"
    identity_ids = null
  }
  tags                          = {
    environment = "dev"
  }
  log_analytics_workspace_name  = "my-log-analytics-workspace"
  hub_storage_account_name      = "my-hub-storage-account"
  storage_account_id            = "storage-account-id"
  log_analytics_workspace_id    = "log-analytics-workspace-id"
  auto_diag_logs                = ["ApplicationLogs", "SecurityLogs"]
  private_endpoint_subnet_id    = "subnet-id"
  private_dns_zone_group        = [
    {
      name                = "zone-group-name"
      private_dns_zone_ids = ["private-dns-zone-id1", "private-dns-zone-id2"]
    }
  ]
  is_manual_connection         = true
}
