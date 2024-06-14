# **Subnet Module**

Terraform module to create a subnet in an Azure virtual network.

## **Description**

This module is used to create a subnet in an Azure virtual network. It requires several attributes in order to be created on Azure, including `subnet_name`, `resource_group_name`, `virtual_network_name`, `address_prefixes`, `private_endpoint_network_policies_enabled`, `private_link_service_network_policies_enabled`, `service_endpoints`, `service_endpoint_policy_ids`, and `delegation_list`.

## **Variable Definitions**

| Name | Description | Type | Required | Default | Example |
|------|-------------|------|----------|---------|:-------:|
| <a name="input_subnet_name"></a>[subnet_name](#input\_subnet_name) | Name of the subnet. | `string` | Yes | `""` | `"my-subnet"` |
| <a name="input_resource_group_name"></a>[resource_group_name](#input\_resource_group_name) | Name of the Azure Resource Group. | `string` | Yes | `""` | `"my-resource-group"` |
| <a name="input_virtual_network_name"></a>[virtual_network_name](#input\_virtual_network_name) | Name of the virtual network. | `string` | Yes | `""` | `"my-virtual-network"` |
| <a name="input_address_prefixes"></a>[address_prefixes](#input\_address_prefixes) | Address prefixes for the subnet. | `list(string)` | Yes | `[]` | `["10.0.1.0/24", "10.0.2.0/24"]` |
| <a name="input_private_endpoint_network_policies_enabled"></a>[private_endpoint_network_policies_enabled](#input\_private_endpoint_network_policies_enabled) | Enable network policies for private endpoints. | `bool` | No | `true` | `false` |
| <a name="input_private_link_service_network_policies_enabled"></a>[private_link_service_network_policies_enabled](#input\_private_link_service_network_policies_enabled) | Enable network policies for private link services. | `bool` | No | `true` | `false` |
| <a name="input_service_endpoints"></a>[service_endpoints](#input\_service_endpoints) | List of service endpoints. | `list(string)` | No | `null` | `["Microsoft.Storage", "Microsoft.Sql"]` |
| <a name="input_service_endpoint_policy_ids"></a>[service_endpoint_policy_ids](#input\_service_endpoint_policy_ids) | List of policy IDs associated with service endpoints. | `list(string)` | No | `null` | `["policy-id-1", "policy-id-2"]` |
| <a name="input_delegation_list"></a>[delegation_list](#input\_delegation_list) | List of delegation. | `list(object({ delegation_name = string service_delegation_name = string service_delegation_actions = optional(list(string),null) }))` | No | `[]` | `[{ delegation_name = "delegation-1", service_delegation_name = "Microsoft.Network/virtualNetworks", service_delegation_actions = ["Microsoft.Network/virtualNetworks/subnets", "Microsoft.Network/virtualNetworks/providers/Microsoft.Authorization/roleAssignments"] }]` |

## **Example Usage**

```hcl
module "subnet" {
  source                              = "tfe.axisb.com/ax-tfe/subnet/azurerm"
  version                             = "X.X.X"
  subnet_name                         = "my-subnet"
  resource_group_name                 = "my-resource-group"
  virtual_network_name                = "my-virtual-network"
  address_prefixes                    = ["10.0.1.0/24", "10.0.2.0/24"]
  private_endpoint_network_policies_enabled = true
  private_link_service_network_policies_enabled = true
  service_endpoints                   = ["Microsoft.Storage", "Microsoft.Sql"]
  service_endpoint_policy_ids         = ["policy-id-1", "policy-id-2"]
  delegation_list                     = [{ delegation_name = "delegation-1", service_delegation_name = "Microsoft.Network/virtualNetworks", service_delegation_actions = ["Microsoft.Network/virtualNetworks/subnets", "Microsoft.Network/virtualNetworks/providers/Microsoft.Authorization/roleAssignments"] }]
}
