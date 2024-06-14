## **Firewall Policy Module**

Terraform module to create a Firewall Policy in Azure.

### **Description**

This module provisions a Firewall Policy in Azure with the specified configurations.

### **Variables**

| Name | Description | Type | Required | Default | Example |
|------|-------------|------|----------|---------|:-------:|
| <a name="input_policy_name"></a>[policy_name](#input\_policy_name) | The ID of the pre-existing Firewall Policy. If provided then a new Firewall policy will not be created. | `string` | No | `null` | `"existing-firewall-policy"` |
| <a name="input_new_policy_name"></a>[new_policy_name](#input\_new_policy_name) | The name of the Firewall Policy. If provided then a new Firewall policy will be created. | `string` | No | `null` | `"new-firewall-policy"` |
| <a name="input_location"></a>[location](#input\_location) | The location of the resource group. | `string` | Yes | `""` | `"East US"` |
| <a name="input_resource_group_name"></a>[resource_group_name](#input\_resource_group_name) | The name of the resource group in which to create the Firewall Policy. | `string` | Yes | `""` | `"my-resource-group"` |
| <a name="input_base_policy_id"></a>[base_policy_id](#input\_base_policy_id) | The ID of the base Firewall Policy. | `string` | No | `null` | `"base-firewall-policy-id"` |
| <a name="input_dns"></a>[dns](#input\_dns) | DNS configuration of the Firewall Policy. | `object` | No | `null` | `{ proxy_enabled = true, servers = ["8.8.8.8", "8.8.4.4"] }` |
| <a name="input_identity"></a>[identity](#input\_identity) | Identity configuration of the Firewall Policy. | `object` | No | `null` | `{ type = "SystemAssigned", identity_ids = ["identity-id"] }` |
| <a name="input_insights"></a>[insights](#input\_insights) | Insights configuration of the Firewall Policy. | `object` | No | `null` | `{ enabled = true, default_log_analytics_workspace_id = "log-analytics-workspace-id", retention_in_days = 30, log_analytics_workspace = { id = "log-analytics-workspace-id", firewall_location = "East US" } }` |
| <a name="input_intrusion_detection"></a>[intrusion_detection](#input\_intrusion_detection) | Intrusion Detection configuration of the Firewall Policy. | `list(object)` | No | `[]` | `[ { mode = "Detection", signature_overrides = [{ id = 1, state = "Disabled" }], traffic_bypass = [{ name = "bypass-rule", protocol = "TCP", destination_addresses = ["10.0.0.1"], destination_ports = ["80"] }], private_ranges = ["10.0.0.0/24"] } ]` |
| <a name="input_private_ip_ranges"></a>[private_ip_ranges](#input\_private_ip_ranges) | A list of private IP ranges to which traffic will not be SNAT. | `list(string)` | No | `[]` | `["10.0.0.0/24", "192.168.0.0/24"]` |
| <a name="input_auto_learn_private_ranges_enabled"></a>[auto_learn_private_ranges_enabled](#input\_auto_learn_private_ranges_enabled) | Whether to automatically learn private ranges. | `bool` | No | `null` | `true` |
| <a name="input_sku"></a>[sku](#input\_sku) | The SKU Tier of the Firewall Policy. Possible values are Standard, Premium, and Basic. | `string` | No | `null` | `"Standard"` |
| <a name="input_tags"></a>[tags](#input\_tags) | A mapping of tags to assign to the Firewall Policy. | `map(string)` | No | `{}` | `{ environment = "dev" }` |
| <a name="input_threat_intelligence_allowlist"></a>[threat_intelligence_allowlist](#input\_threat_intelligence_allowlist) | A list of threat intelligence allowlist. | `list(object)` | No | `[]` | `[ { fqdns = ["example.com"], ip_addresses = ["10.0.0.1"] } ]` |
| <a name="input_threat_intelligence_mode"></a>[threat_intelligence_mode](#input\_threat_intelligence_mode) | The threat intelligence mode of the Firewall Policy. | `string` | No | `"Alert"` | `"Deny"` |
| <a name="input_tls_certificate"></a>[tls_certificate](#input\_tls_certificate) | TLS certificate configuration of the Firewall Policy. | `object` | No | `null` | `{ key_vault_secret_id = "secret-id", name = "certificate-name" }` |
| <a name="input_sql_redirect_allowed"></a>[sql_redirect_allowed](#input\_sql_redirect_allowed) | Allow SQL Redirect. | `bool` | No | `null` | `true` |
| <a name="input_explicit_proxy"></a>[explicit_proxy](#input\_explicit_proxy) | Explicit proxy configuration of the Firewall Policy. | `object` | No | `null` | `{ enabled = true, http_port = 8080, https_port = 8443, enable_pac_file = true, pac_file_port = 8081, pac_file = "pac-file-url" }` |
| <a name="input_policy_rule_collection_group_name"></a>[policy_rule_collection_group_name](#input\_policy_rule_collection_group_name) | The name of the Firewall Policy Rule Collection Group. | `string` | Yes | `""` | `"firewall-rule-collection-group"` |
| <a name="input_priority"></a>[priority](#input\_priority) | The priority of the Firewall Policy Rule Collection Group. | `number` | Yes | `""` | `100` |
| <a name="input_application_rule_collection"></a>[application_rule_collection](#input\_application_rule_collection) | A list of application rule collections. | `list(object)` | No | `[]` | `[ { name = "app-rule-collection", action = "Allow", priority = 100, rule = [{ name = "rule1", protocols = [{ type = "Http", port = 80 }], source_addresses = ["10.0.0.0/24"], destination_addresses = ["192.168.0.0/24"], destination_urls = ["example.com"] }] } ]` |
| <a name="input_network_rule_collection"></a>[network_rule_collection](#input\_network_rule_collection) | A list of network rule collections. | `list(object)` | No | `[]` | `[ { name = "network-rule-collection", action = "Allow", priority = 100, rule = [{ name = "rule1", protocols = ["TCP"], destination_ports = ["80"], source_addresses = ["10.0.0.0/24"], destination_addresses = ["192.168.0.0/24"] }] } ]` |
| <a name="input_nat_rule_collection"></a>[nat_rule_collection](#input\_nat_rule_collection) | A list of NAT rule collections. | `list(object)` | No | `[]` | `[ { name = "nat-rule-collection", action = "Dnat", priority = 100, rule = [{ name = "rule1", protocols = "TCP", source_addresses = ["10.0.0.0/24"], destination_address = "192.168.0.1", destination_ports = ["80"], translated_address = "192.168.1.1", translated_port = "8080" }] } ]` |

### **Example Usage**

```hcl
module "firewall_policy" {
  source                         = "tfe.axisb.com/ax-tfe/firewall-policy/azurerm"
  version                        = "X.X.X"
  policy_name                    = "existing-firewall-policy"
  new_policy_name                = null
  location                       = "East US"
  resource_group_name            = "my-resource-group"
  base_policy_id                 = "base-firewall-policy-id"
  dns                            = { proxy_enabled = true, servers = ["8.8.8.8", "8.8.4.4"] }
  identity                       = { type = "SystemAssigned", identity_ids = ["identity-id"] }
  insights                       = { enabled = true, default_log_analytics_workspace_id = "log-analytics-workspace-id", retention_in_days = 30, log_analytics_workspace = { id = "log-analytics-workspace-id", firewall_location = "East US" } }
  intrusion_detection            = [{ mode = "Detection", signature_overrides = [{ id = 1, state = "Disabled" }], traffic_bypass = [{ name = "bypass-rule", protocol = "TCP", destination_addresses = ["10.0.0.1"], destination_ports = ["80"] }], private_ranges = ["10.0.0.0/24"] }]
  private_ip_ranges              = ["10.0.0.0/24", "192.168.0.0/24"]
  auto_learn_private_ranges_enabled = true
  sku                            = "Standard"
  tags                           = { environment = "dev" }
  threat_intelligence_allowlist  = [{ fqdns = ["example.com"], ip_addresses = ["10.0.0.1"] }]
  threat_intelligence_mode       = "Alert"
  tls_certificate                = { key_vault_secret_id = "secret-id", name = "certificate-name" }
  sql_redirect_allowed           = true
  explicit_proxy                 = { enabled = true, http_port = 8080, https_port = 8443, enable_pac_file = true, pac_file_port = 8081, pac_file = "pac-file-url" }
  policy_rule_collection_group_name = "firewall-rule-collection-group"
  priority                       = 100
  application_rule_collection    = [{ name = "app-rule-collection", action = "Allow", priority = 100, rule = [{ name = "rule1", protocols = [{ type = "Http", port = 80 }], source_addresses = ["10.0.0.0/24"], destination_addresses = ["192.168.0.0/24"], destination_urls = ["example.com"] }] }]
  network_rule_collection        = [{ name = "network-rule-collection", action = "Allow", priority = 100, rule = [{ name = "rule1", protocols = ["TCP"], destination_ports = ["80"], source_addresses = ["10.0.0.0/24"], destination_addresses = ["192.168.0.0/24"] }] }]
  nat_rule_collection            = [{ name = "nat-rule-collection", action = "Dnat", priority = 100, rule = [{ name = "rule1", protocols = "TCP", source_addresses = ["10.0.0.0/24"], destination_address = "192.168.0.1", destination_ports = ["80"], translated_address = "192.168.1.1", translated_port = "8080" }] }]
}
