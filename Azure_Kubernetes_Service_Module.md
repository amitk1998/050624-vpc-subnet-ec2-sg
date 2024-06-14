# **Azure Kubernetes Service Module**

Terraform module to create Azure Kubernetes Service

# **Description**

This module is used to create an Azure Kubernetes Service (AKS). It requires several attributes in order to be created on Azure, including `name`, `location`, `resource_group_name`, etc.

# **Variable Definitions**

| Name | Description | Type | Required | Default | Example |
|------|-------------|------|----------|---------|:-------:|
| <a name="input_name"></a>[name](#input\_name) | The name of the cluster | `string` | Yes | `""` | `"my-aks-cluster"` |
| <a name="input_location"></a>[location](#input\_location) | The location of the cluster | `string` | Yes | `""` | `"East US"` |
| <a name="input_resource_group_name"></a>[resource_group_name](#input\_resource_group_name) | The name of the resource group | `string` | Yes | `""` | `"my-resource-group"` |
| <a name="input_pod_subnet_id"></a>[pod_subnet_id](#input\_pod_subnet_id) | ID of Subnet where pod in the default node pool should exist | `string` | No | `null` | `"subnet-id"` |
| <a name="input_default_node_pool"></a>[default_node_pool](#input\_default_node_pool) | Default node pool config | `object({...})` | Yes | `{}` | See example |
| <a name="input_dns_prefix"></a>[dns_prefix](#input\_dns_prefix) | DNS prefix specified when creating the managed cluster | `string` | No | `null` | `"dns-prefix"` |
| <a name="input_dns_prefix_private_cluster"></a>[dns_prefix_private_cluster](#input\_dns_prefix_private_cluster) | DNS prefix specified when creating the private cluster | `string` | No | `null` | `"private-cluster-dns-prefix"` |
| <a name="input_aci_connector_linux"></a>[aci_connector_linux](#input\_aci_connector_linux) | ACI Connector Linux config | `object({...})` | No | `null` | See example |
| <a name="input_automatic_channel_upgrade"></a>[automatic_channel_upgrade](#input\_automatic_channel_upgrade) | Automatic Channel Upgrade | `string` | No | `null` | `"automatic"` |
| <a name="input_api_server_access_profile"></a>[api_server_access_profile](#input\_api_server_access_profile) | API Server Access Profile | `object({...})` | No | `null` | See example |
| <a name="input_auto_scaler_profile"></a>[auto_scaler_profile](#input\_auto_scaler_profile) | Auto Scaler Profile | `object({...})` | No | `null` | See example |
| <a name="input_azure_active_directory_role_based_access_control"></a>[azure_active_directory_role_based_access_control](#input\_azure_active_directory_role_based_access_control) | Azure Active Directory Role Based Access Control config | `object({...})` | No | `null` | See example |
| <a name="input_azure_policy_enabled"></a>[azure_policy_enabled](#input\_azure_policy_enabled) | Azure Policy Enabled | `bool` | No | `false` | `true` |
| <a name="input_confidential_computing"></a>[confidential_computing](#input\_confidential_computing) | Confidential Computing config | `object({...})` | No | `null` | See example |
| <a name="input_custom_ca_trust_certificates_base64"></a>[custom_ca_trust_certificates_base64](#input\_custom_ca_trust_certificates_base64) | A list of up to 10 base64 encoded CAs that will be added to the trust store on nodes | `list(string)` | No | `null` | `["base64-cert-1", "base64-cert-2"]` |
| <a name="input_disk_encryption_set_id"></a>[disk_encryption_set_id](#input\_disk_encryption_set_id) | Disk Encryption Set ID | `string` | No | `null` | `"disk-encryption-set-id"` |
| <a name="input_edge_zone"></a>[edge_zone](#input\_edge_zone) | Edge Zone | `string` | No | `null` | `"edge-zone"` |
| <a name="input_http_application_routing_enabled"></a>[http_application_routing_enabled](#input\_http_application_routing_enabled) | HTTP Application Routing Enabled | `bool` | No | `null` | `true` |
| <a name="input_http_proxy_config"></a>[http_proxy_config](#input\_http_proxy_config) | HTTP Proxy Configuration | `object({...})` | No | `null` | See example |
| <a name="input_identity"></a>[identity](#input\_identity) | Identity | `object({...})` | No | `null` | See example |
| <a name="input_image_cleaner_enabled"></a>[image_cleaner_enabled](#input\_image_cleaner_enabled) | Specifies whether Image Cleaner is enabled | `bool` | No | `null` | `true` |
| <a name="input_image_cleaner_interval_hours"></a>[image_cleaner_interval_hours](#input\_image_cleaner_interval_hours) | Specifies the frequency of image cleaning | `number` | No | `48` | `24` |
| <a name="input_ingress_application_gateway"></a>[ingress_application_gateway](#input\_ingress_application_gateway) | Ingress Application Gateway | `object({...})` | No | `null` | See example |
| <a name="input_key_management_service"></a>[key_management_service](#input\_key_management_service) | Key Management Service | `object({...})` | No | `null` | See example |
| <a name="input_key_vault_secrets_provider"></a>[key_vault_secrets_provider](#input\_key_vault_secrets_provider) | Key Vault Secrets Provider | `object({...})` | No | `null` | See example |
| <a name="input_kubelet_identity"></a>[kubelet_identity](#input\_kubelet_identity) | Kubelet Identity configuration | `object({...})` | No | `null` | See example |
| <a name="input_kubernetes_version"></a>[kubernetes_version](#input\_kubernetes_version) | Kubernetes Version | `string` | No | `null` | `"1.21.2"` |
| <a name="input_linux_profile"></a>[linux_profile](#input\_linux_profile) | Linux Profile | `object({...})` | No | `null` | See example |
| <a name="input_local_account_disabled"></a>[local_account_disabled](#input\_local_account_disabled) | Local Account Disabled | `bool` | No | `null` | `true` |
| <a name="input_maintenance_window"></a>[maintenance_window](#input\_maintenance_window) | Maintenance Window config | `object({...})` | No | `null` | See example |
| <a name="input_maintenance_window_auto_upgrade"></a>[maintenance_window_auto_upgrade](#input\_maintenance_window_auto_upgrade) | Maintenance Window Auto Upgrade config | `object({...})` | No | `null` | See example |
| <a name="input_maintenance_window_node_os"></a>[maintenance_window_node_os](#input\_maintenance_window_node_os) | Maintenance Window Node OS config | `object({...})` | No | `null` | See example |
| <a name="input_microsoft_defender"></a>[microsoft_defender](#input\_microsoft_defender) | Microsoft Defender config | `object({...})` | No | `null` | See example |
| <a name="input_monitor_metrics"></a>[monitor_metrics](#input\_monitor_metrics) | Monitor Metrics config | `object({...})` | No | `null` | See example |
| <a name="input_pod_cidrs"></a>[pod_cidrs](#input\_pod_cidrs) | List of CIDR to be used for Pods | `list(string)` | No | `[]` | `["10.244.0.0/16", "10.245.0.0/16"]` |
| <a name="input_network_profile"></a>[network_profile](#input\_network_profile) | Network Profile config | `object({...})` | No | `null` | See example |
| <a name="input_node_os_channel_upgrade"></a>[node_os_channel_upgrade](#input\_node_os_channel_upgrade) | The upgrade channel for this Kubernetes Cluster Nodes' OS Image | `string` | No | `null` | `"rapid"` |
| <a name="input_node_resource_group"></a>[node_resource_group](#input\_node_resource_group) | The name of the Resource Group where the Kubernetes Nodes should exist | `string` | No | `null` | `"node-resource-group"` |
| <a name="input_oidc_issuer_enabled"></a>[oidc_issuer_enabled](#input\_oidc_issuer_enabled) | Enable or Disable the OIDC issuer URL | `bool` | No | `null` | `true` |
| <a name="input_oms_agent"></a>[oms_agent](#input\_oms_agent) | Enable or Disable the OMS Agent | `object({...})` | No | `null` | See example |
| <a name="input_open_service_mesh_enabled"></a>[open_service_mesh_enabled](#input\_open_service_mesh_enabled) | Enable or Disable the Open Service Mesh | `bool` | No | `null` | `true` |
| <a name="input_pod_security_policy"></a>[pod_security_policy](#input\_pod_security_policy) | Enable or Disable the Pod Security Policy | `bool` | No | `null` | `true` |
| <a name="input_private_cluster_enabled"></a>[private_cluster_enabled](#input\_private_cluster_enabled) | Enable or Disable the Private Cluster | `bool` | No | `null` | `true` |
| <a name="input_private_dns_zone_id"></a>[private_dns_zone_id](#input\_private_dns_zone_id) | Private DNS Zone ID | `string` | No | `null` | `"private-dns-zone-id"` |
| <a name="input_proxy_auto_configuration_enabled"></a>[proxy_auto_configuration_enabled](#input\_proxy_auto_configuration_enabled) | Enable or Disable Proxy Auto Configuration | `bool` | No | `null` | `true` |
| <a name="input_role_assignment"></a>[role_assignment](#input\_role_assignment) | Role Assignment | `object({...})` | No | `null` | See example |
| <a name="input_service_principal"></a>[service_principal](#input\_service_principal) | Service Principal | `object({...})` | No | `null` | See example |
| <a name="input_sgx_enabled"></a>[sgx_enabled](#input\_sgx_enabled) | Enable or Disable SGX | `bool` | No | `null` | `true` |
| <a name="input_ssh"></a>[ssh](#input\_ssh) | SSH config | `object({...})` | No | `null` | See example |
| <a name="input_system_node_pool"></a>[system_node_pool](#input\_system_node_pool) | System Node Pool config | `object({...})` | No | `null` | See example |
| <a name="input_tags"></a>[tags](#input\_tags) | A mapping of tags to assign to the resource. | `map(string)` | No | `{}` | `{}` |
| <a name="input_tls_profile"></a>[tls_profile](#input\_tls_profile) | TLS Profile | `object({...})` | No | `null` | See example |
| <a name="input_user_assigned_identity"></a>[user_assigned_identity](#input\_user_assigned_identity) | User Assigned Identity | `object({...})` | No | `null` | See example |
| <a name="input_windows_profile"></a>[windows_profile](#input\_windows_profile) | Windows Profile | `object({...})` | No | `null` | See example |
| <a name="input_workspace_id"></a>[workspace_id](#input\_workspace_id) | Workspace ID | `string` | No | `null` | `"workspace-id"` |

# **Usage**

```hcl
module "aks" {
  source = "path/to/module"

  name                 = "my-aks-cluster"
  location             = "East US"
  resource_group_name  = "my-resource-group"
  default_node_pool    = {
    name            = "default"
    vm_size         = "Standard_DS2_v2"
    node_count      = 3
    type            = "VirtualMachineScaleSets"
    os_disk_size_gb = 30
  }
}
