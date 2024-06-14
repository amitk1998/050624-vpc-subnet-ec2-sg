# **Azure Virtual Network Module**

Terraform module to create Virtual Network on Azure

# **Description**
 
 This module is basically used to create Virtual Network onAzure.
 It requires few attributes in order to be created on Azure `Virtual Network`,`address_space`,`location`,`name `,`name ` etc.

 # **Variable Defination**

| Name | Description | Type | Required | Default | Example |
|------|-------------|------|----------|---------|:-------:|
| <a name="input_address_space"></a>[address_space](#input\address_space)| Address space for the virtual network. | `string` | Yes | `N/A` | `N/A` |
| <a name="input_name"></a>[name](#input\_name)|  Name. | `string` | Yes | `N/A` | `N/A` |
| <a name="input_resource_group_name"></a>[resource_group_name](#input\_resource_group_name)| resource_group_name. | `string` | Yes | `N/A` | `N/A` |
| <a name="input_Location"></a>[Location](#input\_Location)| Azure region where the virtual network will be created. | `string` | Yes | `N/A` | `N/A` |
| <a name="input_bgp_community"></a>[bgp_community](#input\_bgp_community)| bgp_community. | `string` | No | `null` | `null` | 
| <a name="input_ddos_protection_plan_id "></a>[disable\_ddos_protection_plan_id ](#input\_disable\_ddos_protection_plan_id )| ID of the DDoS protection plan to associate with the virtual network. | `String` | No |  `N/A` |  `N/A` |
|
| <a name="input_dns_servers "></a>[dns_servers ](#input\_dns_servers )| dns_servers . | `list(string)` | No | `[ ]` | `[ ]` |
<a name="input_encryption  "></a>[encryption  ](#input\_encryption  )| Specifies if encrypted vnet allows Vm that does not support encryption . | <pre><code>list(object({<br>  enforcement              = string<br> }))</code></pre> | No | `[{}]` | `[{} ]` |
<a name="input_tags  "></a>[Tags ](#input\_Tags  )| Tags For Virtual Network. | `map(string)` | No | `{}` | `{Name = "tag-name"}` |



## **Example Usage**

```hcl

module "vnet" { 
  source  = "tfe.axisb.com/ax-tfe/vnet/azurerm"
  version = "X.X.X"
  name = "vnet_Name"
  resource_group_name = "resource_group_name"
  location = "Central India"
  address_space = ["10.0.32.0/24"]
}

```