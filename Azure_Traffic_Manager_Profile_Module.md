## **Azure Traffic Manager Profile Module**

Terraform module to create an Azure Traffic Manager Profile.

## **Description**

This module is used to create an Azure Traffic Manager Profile. It requires several attributes in order to be created on Azure, including `name`, `resource_group_name`, `profile_status`, `traffic_view_enabled`, `traffic_routing_method`, `max_return`, `dns_config`, `monitor_config`, and `tags`.

## **Variable Definitions**

| Name | Description | Type | Required | Default | Example |
|------|-------------|------|----------|---------|:-------:|
| <a name="input_name"></a>[name](#input\_name) | Name of the Traffic Manager profile. | `string` | Yes | `""` | `"my-traffic-manager"` |
| <a name="input_resource_group_name"></a>[resource_group_name](#input\_resource_group_name) | Name of the resource group. | `string` | Yes | `""` | `"my-resource-group"` |
| <a name="input_profile_status"></a>[profile_status](#input\_profile_status) | Status of the profile. | `string` | No | `"Enabled"` | `"Disabled"` |
| <a name="input_traffic_view_enabled"></a>[traffic_view_enabled](#input\_traffic_view_enabled) | Traffic view is enabled for the Traffic Manager profile. | `string` | No | `null` | `"Enabled"` |
| <a name="input_traffic_routing_method"></a>[traffic_routing_method](#input\_traffic_routing_method) | Specific the algorithm used for the route traffic. | `string` | Yes | `""` | `"Performance"` |
| <a name="input_max_return"></a>[max_return](#input\_max_return) | The amount of endpoint return for DNS queries to profiler. | `number` | No | `null` | `5` |
| <a name="input_dns_config"></a>[dns_config](#input\_dns_config) | DNS configuration of the Profile. | `object({ relative_name = string, ttl = string })` | Yes | `{}` | `{ relative_name = "example", ttl = "3600" }` |
| <a name="input_monitor_config"></a>[monitor_config](#input\_monitor_config) | Monitoring configuration for the profile. | `object({ protocol = string, port = number, path = optional(string), expected_status_code_ranges = optional(list(string)), interval_in_seconds = optional(number), timeout_in_seconds = optional(number), tolerated_number_of_failures = optional(number), custom_header = optional(list(object({ name = string, value = string }))) })` | No | `null` | See example below |
| <a name="input_tags"></a>[tags](#input\_tags) | A map of tags for the Traffic Manager. | `map(string)` | No | `{}` | `{ environment = "dev" }` |

### **Azure Endpoint Variables**

| Name | Description | Type | Required | Default | Example |
|------|-------------|------|----------|---------|:-------:|
| <a name="input_create_azure_endpoint"></a>[create_azure_endpoint](#input\_create_azure_endpoint) | Flag to create Azure Endpoint. | `bool` | No | `false` | `true` |
| <a name="input_azure_endpoint_name"></a>[azure_endpoint_name](#input\_azure_endpoint_name) | Name of the Azure endpoint. | `string` | No | `null` | `"my-azure-endpoint"` |
| <a name="input_weight"></a>[weight](#input\_weight) | How much traffic should be distributed to this endpoint. | `number` | No | `null` | `50` |
| <a name="input_target_resource_id"></a>[target_resource_id](#input\_target_resource_id) | The id of the Resource which should be used as a target. | `string` | No | `null` | `"resource-id"` |
| <a name="input_endpoint_enabled"></a>[endpoint_enabled](#input\_endpoint_enabled) | Is endpoint enabled. | `bool` | No | `true` | `false` |
| <a name="input_geo_mappings"></a>[geo_mappings](#input\_geo_mappings) | The List of Geographical Regions used to distribute traffic. | `list(string)` | No | `null` | `["US", "EU"]` |
| <a name="input_priority"></a>[priority](#input\_priority) | Priority of the endpoint. | `number` | No | `null` | `1` |
| <a name="input_custom_header"></a>[custom_header](#input\_custom_header) | Custom header block. | `list(object({ name = string, value = string }))` | No | `null` | See example below |
| <a name="input_subnet"></a>[subnet](#input\_subnet) | Subnet block. | `list(object({ first = string, last = optional(string), scope = optional(string) }))` | No | `null` | See example below |

### **External Endpoint Variables**

| Name | Description | Type | Required | Default | Example |
|------|-------------|------|----------|---------|:-------:|
| <a name="input_create_external_endpoint"></a>[create_external_endpoint](#input\_create_external_endpoint) | Flag to create External Endpoint. | `bool` | No | `false` | `true` |
| <a name="input_external_endpoint_name"></a>[external_endpoint_name](#input\_external_endpoint_name) | Name of the external endpoint. | `string` | No | `null` | `"my-external-endpoint"` |
| <a name="input_external_weight"></a>[external_weight](#input\_external_weight) | How much traffic should be distributed to this endpoint. | `number` | No | `null` | `50` |
| <a name="input_external_target"></a>[external_target](#input\_external_target) | The external target. | `string` | No | `null` | `"https://example.com"` |
| <a name="input_external_endpoint_location"></a>[external_endpoint_location](#input\_external_endpoint_location) | External endpoint location. | `string` | No | `null` | `"West US"` |
| <a name="input_external_endpoint_enabled"></a>[external_endpoint_enabled](#input\_external_endpoint_enabled) | Is endpoint enabled. | `bool` | No | `true` | `false` |
| <a name="input_external_geo_mappings"></a>[external_geo_mappings](#input\_external_geo_mappings) | The List of Geographical Regions used to distribute traffic. | `list(string)` | No | `null` | `["US", "EU"]` |
| <a name="input_external_priority"></a>[external_priority](#input\_external_priority) | Priority of the endpoint. | `number` | No | `null` | `1` |
| <a name="input_external_custom_header"></a>[external_custom_header](#input\_external_custom_header) | Custom header block. | `list(object({ name = string, value = string }))` | No | `null` | See example below |
| <a name="input_external_subnet"></a>[external_subnet](#input\_external_subnet) | Subnet block. | `list(object({ first = string, last = optional(string), scope = optional(string) }))` | No | `null` | See example below |

### **Nested Endpoint Variables**

| Name | Description | Type | Required | Default | Example |
|------|-------------|------|----------|---------|:-------:|
| <a name="input_create_nested_external_endpoint"></a>[create_nested_external_endpoint](#input\_create_nested_external_endpoint) | Flag to create Nested Endpoint. | `bool` | No | `false` | `true` |
| <a name="input_nested_endpoint_name"></a>[nested_endpoint_name](#input\_nested_endpoint_name) | Name of the nested endpoint. | `string` | No | `null` | `"my-nested-endpoint"` |
| <a name="input_nested_weight"></a>[nested_weight](#input\_nested_weight) | How much traffic should be distributed to this endpoint. | `number` | No | `null` | `50` |
| <a name="input_nested_target_resource_id"></a>[nested_target_resource_id](#input\_nested_target_resource_id) | The target resource id. | `string` | No | `null` | `"resource-id"` |
| <a name="input_nested_endpoint_location"></a>[nested_endpoint_location](#input\_nested_endpoint_location) | Nested endpoint location. | `string` | No | `null` | `"East US"` |
| <a name="input_minimum_child_endpoints"></a>[minimum_child_endpoints](#input\_minimum_child_endpoints) | Minimum number of child endpoints. | `number` | No | `null` | `2` |
| <a name="input_minimum_required_child_endpoints_ipv4"></a>[minimum_required_child_endpoints_ipv4](#input\_minimum_required_child_endpoints_ipv4) | Minimum number of IPv4 endpoints. | `number` | No | `null` | `2` |
| <a name="input_minimum_required_child_endpoints_ipv6"></a>[minimum_required_child_endpoints_ipv6](#input\_minimum_required_child_endpoints_ipv6) | Minimum number of IPv6 endpoints. | `number` | No | `null` | `1` |
| <a name="input_nested_endpoint_enabled"></a>[nested_endpoint_enabled](#input\_nested_endpoint_enabled) | Is endpoint enabled. | `bool` | No | `true` | `false` |
| <a name="input_nested_geo_mappings"></a>[nested_geo_mappings](#input\_nested_geo_mappings) | The List of Geographical Regions used to distribute traffic. | `list(string)` | No | `null` | `["US", "EU"]` |
| <a name="input_nested_priority"></a>[nested_priority](#input\_nested_priority) | Priority of the endpoint. | `number` | No | `null` | `1` |
| <a name="input_nested_custom_header"></a>[nested_custom_header](#input\_nested_custom_header) | Custom header block. | `list(object({ name = string, value = string }))` | No | `null` | See example below |
| <a name="input_nested_subnet"></a>[nested_subnet](#input\_nested_subnet) | Subnet block. | `list(object({ first = string, last = optional(string), scope = optional(string) }))` | No | `null` | See example below |

## **Example Usage**

```hcl
module "traffic_manager" {
  source                     = "tfe.axisb.com/ax-tfe/traffic-manager/azurerm"
  version                    = "X.X.X"
  name                       = "my-traffic-manager"
  resource_group_name        = "my-resource-group"
  profile_status             = "Enabled"
  traffic_view_enabled       = "Enabled"
  traffic_routing_method     = "Performance"
  max_return                 = 5
  dns_config = {
    relative_name = "example"
    ttl           = "3600"
  }
  monitor_config = {
    protocol                     = "HTTP"
    port                         = 80
    path                         = "/"
    expected_status_code_ranges  = ["200-299"]
    interval_in_seconds          = 30
    timeout_in_seconds           = 10
    tolerated_number_of_failures = 3
    custom_header                = [
      {
        name  = "X-Custom-Header"
        value = "Value"
      }
    ]
  }
  tags = {
    environment = "dev"
  }

  # Azure Endpoint
  create_azure_endpoint   = true
  azure_endpoint_name     = "my-azure-endpoint"
  weight                  = 50
  target_resource_id      = "resource-id"
  endpoint_enabled        = false
  geo_mappings            = ["US", "EU"]
  priority                = 1
  custom_header           = [
    {
      name  = "X-Custom-Header"
      value = "Value"
    }
  ]
  subnet = [
    {
      first = "192.168.1.0"
      last  = "192.168.1.255"
      scope = "Public"
    }
  ]

  # External Endpoint
  create_external_endpoint    = true
  external_endpoint_name      = "my-external-endpoint"
  external_weight             = 50
  external_target             = "https://example.com"
  external_endpoint_location  = "West US"
  external_endpoint_enabled   = false
  external_geo_mappings       = ["US", "EU"]
  external_priority           = 1
  external_custom_header      = [
    {
      name  = "X-Custom-Header"
      value = "Value"
    }
  ]
  external_subnet = [
    {
      first = "192.168.2.0"
      last  = "192.168.2.255"
      scope = "Public"
    }
  ]

  # Nested Endpoint
  create_nested_external_endpoint     = true
  nested_endpoint_name                = "my-nested-endpoint"
  nested_weight                       = 50
  nested_target_resource_id           = "resource-id"
  nested_endpoint_location            = "East US"
  minimum_child_endpoints             = 2
  minimum_required_child_endpoints_ipv4 = 2
  minimum_required_child_endpoints_ipv6 = 1
  nested_endpoint_enabled             = false
  nested_geo_mappings                 = ["US", "EU"]
  nested_priority                     = 1
  nested_custom_header                = [
    {
      name  = "X-Custom-Header"
      value = "Value"
    }
  ]
  nested_subnet = [
    {
      first = "192.168.3.0"
      last  = "192.168.3.255"
      scope = "Public"
    }
  ]
}
