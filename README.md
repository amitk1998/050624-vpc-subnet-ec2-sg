# **Virtual Machine Module**

Terraform module to create a virtual machine in Azure.

## **Description**

This module is used to create a virtual machine in Azure. It requires several attributes in order to be created on Azure, including `generate_admin_ssh_key`, `rsa_algorithm`, `rsa_bits`, `os_flavor`, `virtual_machine_name`, `virtual_machine_size`, `admin_username`, `admin_password`, `disable_password_authentication`, `os_disk_storage_account_type`, `os_disk_caching`, `disk_encryption_set_id`, `security_encryption_type`, `secure_vm_disk_encryption_set_id`, `disk_size_gb`, `enable_os_disk_write_accelerator`, `custom_data`, `availability_set_id`, `enable_vm_availability_set`, `enable_encryption_at_host`, `dedicated_host_id`, `vm_availability_zone`, `tags`, `managed_identity_type`, `managed_identity_ids`, `enable_boot_diagnostics`, `storage_account_name`, `winrm_protocol`, `key_vault_certificate_secret_url`, `additional_unattend_content`, `additional_unattend_content_setting`, `enable_ultra_ssd_data_disk_storage_support`, `license_type`, `patch_mode`, `vm_time_zone`, `storage_account_uri`, `source_image_reference`, `enable_proximity_placement_group`, `os_disk_name`, `source_image_id`, `enable_automatic_updates`, `proximity_placement_group_id`, `resource_group_name`, `location`, `key_vault_id`, `network_interface_ids`, `admin_ssh_key_data`, `create_VM_extention`, `VMExtention_name`, `publisher`, `type`, `type_handler_version`, `auto_upgrade_minor_version`, `certificates`, `settings`, and `protected_settings`.

## **Variable Definitions**

| Name | Description | Type | Required | Default | Example |
|------|-------------|------|----------|---------|:-------:|
| <a name="input_generate_admin_ssh_key"></a>[generate_admin_ssh_key](#input\_generate_admin_ssh_key) | Whether to generate an admin SSH key. | `bool` | No | `false` | `true` |
| <a name="input_rsa_algorithm"></a>[rsa_algorithm](#input\_rsa_algorithm) | The RSA algorithm to use for generating the private key. | `string` | No | `"RSA"` | `"RSA"` |
| <a name="input_rsa_bits"></a>[rsa_bits](#input\_rsa_bits) | The number of bits for the RSA private key. | `number` | No | `4096` | `2048` |
| <a name="input_os_flavor"></a>[os_flavor](#input\_os_flavor) | Operating system flavor (e.g., 'linux' or 'windows'). | `string` | Yes | `""` | `"linux"` |
| <a name="input_virtual_machine_name"></a>[virtual_machine_name](#input\_virtual_machine_name) | Name of the virtual machine. | `string` | Yes | `""` | `"my-vm"` |
| <a name="input_virtual_machine_size"></a>[virtual_machine_size](#input\_virtual_machine_size) | Size of the virtual machine. | `string` | Yes | `""` | `"Standard_DS1_v2"` |
| <a name="input_admin_username"></a>[admin_username](#input\_admin_username) | Admin username for the virtual machine. | `string` | Yes | `""` | `"admin"` |
| <a name="input_admin_password"></a>[admin_password](#input\_admin_password) | Admin password for the virtual machine. | `string` | Yes | `""` | `"Password123!"` |
| <a name="input_disable_password_authentication"></a>[disable_password_authentication](#input\_disable_password_authentication) | Whether to disable password authentication. | `bool` | No | `false` | `true` |
| <a name="input_os_disk_storage_account_type"></a>[os_disk_storage_account_type](#input\_os_disk_storage_account_type) | Storage account type for the OS disk. | `string` | No | `""` | `"Standard_LRS"` |
| <a name="input_os_disk_caching"></a>[os_disk_caching](#input\_os_disk_caching) | Caching type for the OS disk. | `string` | No | `""` | `"ReadWrite"` |
| <a name="input_disk_encryption_set_id"></a>[disk_encryption_set_id](#input\_disk_encryption_set_id) | ID of the disk encryption set. | `string` | No | `null` | `"disk-encryption-set-id"` |
| <a name="input_security_encryption_type"></a>[security_encryption_type](#input\_security_encryption_type) | Security encryption type for the OS disk. | `string` | No | `null` | `"EncryptionAtRestWithCustomerKey"` |
| <a name="input_secure_vm_disk_encryption_set_id"></a>[secure_vm_disk_encryption_set_id](#input\_secure_vm_disk_encryption_set_id) | ID of the secure VM disk encryption set. | `string` | No | `null` | `"secure-vm-disk-encryption-set-id"` |
| <a name="input_disk_size_gb"></a>[disk_size_gb](#input\_disk_size_gb) | Size of the OS disk in GB. | `number` | No | `null` | `128` |
| <a name="input_enable_os_disk_write_accelerator"></a>[enable_os_disk_write_accelerator](#input\_enable_os_disk_write_accelerator) | Whether to enable OS disk write accelerator. | `bool` | No | `false` | `true` |
| <a name="input_custom_data"></a>[custom_data](#input\_custom_data) | Custom data to be used when provisioning the virtual machine. | `string` | No | `null` | `"echo 'Hello, World!' > /tmp/hello.txt"` |
| <a name="input_availability_set_id"></a>[availability_set_id](#input\_availability_set_id) | ID of the availability set for the virtual machine. | `string` | No | `null` | `"availability-set-id"` |
| <a name="input_enable_vm_availability_set"></a>[enable_vm_availability_set](#input\_enable_vm_availability_set) | Whether to enable the availability set for the virtual machine. | `bool` | No | `false` | `true` |
| <a name="input_enable_encryption_at_host"></a>[enable_encryption_at_host](#input\_enable_encryption_at_host) | Whether to enable encryption at host for the virtual machine. | `bool` | No | `false` | `true` |
| <a name="input_dedicated_host_id"></a>[dedicated_host_id](#input\_dedicated_host_id) | ID of the dedicated host for the virtual machine. | `string` | No | `null` | `"dedicated-host-id"` |
| <a name="input_vm_availability_zone"></a>[vm_availability_zone](#input\_vm_availability_zone) | Availability zone for the virtual machine. | `string` | No | `null` | `"1"` |
| <a name="input_tags"></a>[tags](#input\_tags) | A map of tags to apply to the virtual machine. | `map(string)` | No | `{}` | `{"environment": "production", "app": "web"}` |
| <a name="input_managed_identity_type"></a>[managed_identity_type](#input\_managed_identity_type) | Type of managed identity for the virtual machine. | `string` | No | `null` | `"SystemAssigned"` |
| <a name="input_managed_identity_ids"></a>[managed_identity_ids](#input\_managed_identity_ids) | List of managed identity IDs for the virtual machine. | `list(string)` | No | `[]` | `["managed-identity-id-1", "managed-identity-id-2"]` |
| <a name="input_enable_boot_diagnostics"></a>[enable_boot_diagnostics](#input\_enable_boot_diagnostics) | Whether to enable boot diagnostics for the virtual machine. | `bool` | No | `false` | `true` |
| <a name="input_storage_account_name"></a>[storage_account_name](#input\_storage_account_name) | Name of the storage account for boot diagnostics. | `string` | No | `null` | `"bootdiagnosticsstorage"` |
| <a name="input_winrm_protocol"></a>[winrm_protocol](#input\_winrm_protocol) | WinRM protocol (e.g., 'Http' or 'Https'). | `string` | No | `null` | `"Https"` |
| <a name="input_key_vault_certificate_secret_url"></a>[key_vault_certificate_secret_url](#input\_key_vault_certificate_secret_url) | URL of the Key Vault certificate secret for WinRM over HTTPS. | `string` | No | `null` | `"https://mykeyvault.vault.azure.net/secrets/mycertificate"` |
| <a name="input_additional_unattend_content"></a>[additional_unattend_content](#input\_additional_unattend_content) | Additional unattend content for Windows virtual machines. | `string` | No | `null` | `"additional content"` |
| <a name="input_additional_unattend_content_setting"></a>[additional_unattend_content_setting](#input\_additional_unattend_content_setting) | Setting for additional unattend content for Windows virtual machines. | `string` | No | `null` | `"MyUnattendContent"` |
| <a name="input_enable_ultra_ssd_data_disk_storage_support"></a>[enable_ultra_ssd_data_disk_storage_support](#input\_enable_ultra_ssd_data_disk_storage_support) | Whether to enable Ultra SSD data disk storage support. | `bool` | No | `false` | `true` |
| <a name="input_license_type"></a>[license_type](#input\_license_type) | License type for Windows virtual machines. | `string` | No | `null` | `"Windows_Server"` |
| <a name="input_patch_mode"></a>[patch_mode](#input\_patch_mode) | Patch mode for Windows virtual machines. | `string` | No | `null` | `"AutomaticByOS"` |
| <a name="input_vm_time_zone"></a>[vm_time_zone](#input\_vm_time_zone) | Time zone for Windows virtual machines. | `string` | No | `null` | `"Eastern Standard Time"` |
| <a name="input_storage_account_uri"></a>[storage_account_uri](#input\_storage_account_uri) | URI of the storage account for boot diagnostics. | `string` | No | `null` | `"https://mystorageaccount.blob.core.windows.net/"` |
| <a name="input_source_image_reference"></a>[source_image_reference](#input\_source_image_reference) | Source image reference distribution properties. | `object({ publisher = string offer = string sku = string version = string })` | No | `null` | `{ publisher = "Canonical", offer = "UbuntuServer", sku = "18.04-LTS", version = "latest" }` |
| <a name="input_enable_proximity_placement_group"></a>[enable_proximity_placement_group](#input\_enable_proximity_placement_group) | Whether to enable proximity placement group for the virtual machine. | `bool` | No | `false` | `true` |
| <a name="input_os_disk_name"></a>[os_disk_name](#input\_os_disk_name) | Name of the OS disk. | `string` | No | `"osdisk"` | `"osdisk"` |
| <a name="input_source_image_id"></a>[source_image_id](#input\_source_image_id) | ID of the source image to use for virtual machine creation. | `string` | No | `null` | `"source-image-id"` |
| <a name="input_enable_automatic_updates"></a>[enable_automatic_updates](#input\_enable_automatic_updates) | Whether to enable automatic OS updates for Windows virtual machines. | `bool` | No | `true` | `true` |
| <a name="input_proximity_placement_group_id"></a>[proximity_placement_group_id](#input\_proximity_placement_group_id) | ID of the proximity placement group if `enable_proximity_placement_group` is true, otherwise an empty string. | `string` | No | `null` | `"proximity-placement-group-id"` |
| <a name="input_resource_group_name"></a>[resource_group_name](#input\_resource_group_name) | The name of the Azure resource group. | `string` | Yes | `""` | `"my-resource-group"` |
| <a name="input_location"></a>[location](#input\_location) | The Azure region where the resource group is located. | `string` | Yes | `""` | `"eastus"` |
| <a name="input_key_vault_id"></a>[key_vault_id](#input\_key_vault_id) | Key vault key id. | `string` | No | `null` | `"key-vault-id"` |
| <a name="input_network_interface_ids"></a>[network_interface_ids](#input\_network_interface_ids) | A list of network interface IDs for the virtual machine. | `list(string)` | No | `[]` | `["nic-id-1", "nic-id-2"]` |
| <a name="input_admin_ssh_key_data"></a>[admin_ssh_key_data](#input\_admin_ssh_key_data) | SSH key data for admin user. | `string` | No | `null` | `"ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQD..."` |
| <a name="input_create_VM_extention"></a>[create_VM_extention](#input\_create_VM_extention) | Set to true to create the Virtual machine Extention. | `bool` | No | `false` | `true` |
| <a name="input_VMExtention_name"></a>[VMExtention_name](#input\_VMExtention_name) | The name of the VM extension. | `string` | No | `""` | `"vm-extension-name"` |
| <a name="input_publisher"></a>[publisher](#input\_publisher) | The publisher of the VM extension. | `string` | No | `""` | `"Microsoft.EnterpriseCloud.Monitoring"` |
| <a name="input_type"></a>[type](#input\_type) | The type of the VM extension. | `string` | No | `""` | `"vm-extension-type"` |
| <a name="input_type_handler_version"></a>[type_handler_version](#input\_type_handler_version) | The version of the VM extension type handler. | `string` | No | `null` | `"1.0"` |
| <a name="input_auto_upgrade_minor_version"></a>[auto_upgrade_minor_version](#input\_auto_upgrade_minor_version) | Set to true to automatically upgrade the minor version of the extension. | `bool` | No | `true` | `false` |
| <a name="input_certificates"></a>[certificates](#input\_certificates) | Certificates for the extension. | `object({ store = optional(string) url = string key_vault_id = string })` | No | `null` | `{ store = "My" url = "https://mykeyvault.vault.azure.net/secrets/mycertificate" key_vault_id = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/my-resource-group/providers/Microsoft.KeyVault/vaults/my-keyvault" }` |
| <a name="input_settings"></a>[settings](#input\_settings) | The settings passed to the extension. | `string` | No | `null` | `"{\"setting1\": \"value1\", \"setting2\": \"value2\"}"` |
| <a name="input_protected_settings"></a>[protected_settings](#input\_protected_settings) | The protected_settings passed to the extension. | `string` | No | `null` | `"{\"protectedsetting1\": \"value1\", \"protectedsetting2\": \"value2\"}"` |

## **Example Usage**

```hcl
module "virtual_machine" {
  source                          = "tfe.axisb.com/ax-tfe/virtual-machine/azurerm"
  version                         = "X.X.X"
  generate_admin_ssh_key          = false
  rsa_algorithm                   = "RSA"
  rsa_bits                        = 4096
  os_flavor                       = "linux"
  virtual_machine_name            = "my-vm"
  virtual_machine_size            = "Standard_DS1_v2"
  admin_username                  = "admin"
  admin_password                  = "Password123!"
  disable_password_authentication = false
  os_disk_storage_account_type    = "Standard_LRS"
  os_disk_caching                 = "ReadWrite"
  disk_size_gb                    = 128
  custom_data                     = "echo 'Hello, World!' > /tmp/hello.txt"
  availability_set_id             = "availability-set-id"
  enable_vm_availability_set     = true
  enable_boot_diagnostics         = true
  storage_account_name            = "bootdiagnosticsstorage"
  winrm_protocol                  = "Https"
  key_vault_certificate_secret_url= "https://mykeyvault.vault.azure.net/secrets/mycertificate"
  resource_group_name             = "my-resource-group"
  location                        = "eastus"
  network_interface_ids           = ["nic-id-1", "nic-id-2"]
}
