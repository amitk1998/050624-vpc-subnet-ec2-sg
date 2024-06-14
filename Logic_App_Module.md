## **Logic App Module**

Terraform module to deploy a Logic App in Azure.

## **Description**

This module is used to deploy a Logic App in Azure. It requires several attributes in order to be created on Azure, including `logic_app_name`, `resource_group_name`, `location`, `app_service_plan_id`, `app_settings`, `use_extension_bundle`, `bundle_version`, `connection_string`, `client_affinity_enabled`, `client_certificate_mode`, `enabled`, `https_only`, `identity`, `site_config`, `storage_account_name`, `storage_account_access_key`, `storage_account_share_name`, `logic_app_version`, `virtual_network_subnet_id`, and `tags`.

### **Workflow Parameters**

| Name | Description | Type | Required | Default | Example |
|------|-------------|------|----------|---------|:-------:|
| <a name="input_workflow_name"></a>[workflow_name](#input\_workflow_name) | Name of the workflow. | `string` | No | `null` | `"my-workflow"` |
| <a name="input_access_control"></a>[access_control](#input\_access_control) | Access control block. | `object({ action = optional(object({ allowed_caller_ip_address_range = string })), content = optional(object({ allowed_caller_ip_address_range = string })), trigger = optional(object({ allowed_caller_ip_address_range = string })), workflow_management = optional(object({ allowed_caller_ip_address_range = string })) })` | No | `null` | See example below |
| <a name="input_workflow_identity"></a>[workflow_identity](#input\_workflow_identity) | Identity block. | `object({ type = string, identity_ids = optional(list(string)) })` | No | `null` | See example below |
| <a name="input_integration_service_environment_id"></a>[integration_service_environment_id](#input\_integration_service_environment_id) | The ID of the Integration Service Environment. | `string` | No | `null` | `"integration-service-id"` |
| <a name="input_logic_app_integration_account_id"></a>[logic_app_integration_account_id](#input\_logic_app_integration_account_id) | The ID of the Logic App Integration Account. | `string` | No | `null` | `"integration-account-id"` |
| <a name="input_workflow_enabled"></a>[workflow_enabled](#input\_workflow_enabled) | Whether the Logic App is enabled. | `bool` | No | `true` | `false` |
| <a name="input_workflow_parameters"></a>[workflow_parameters](#input\_workflow_parameters) | A map of key-value pairs to assign as parameters to the Logic App. | `map(string)` | No | `null` | `{ param1 = "value1", param2 = "value2" }` |
| <a name="input_workflow_schema"></a>[workflow_schema](#input\_workflow_schema) | The schema of the Logic App. | `string` | No | `null` | `"schema-definition"` |
| <a name="input_workflow_version"></a>[workflow_version](#input\_workflow_version) | The version of the Logic App. | `string` | No | `"1.0.0.0"` | `"2.0.0.0"` |
| <a name="input_parameters"></a>[parameters](#input\_parameters) | A map of key-value pairs to assign as parameters to the Logic App. | `map(string)` | No | `null` | `{ param1 = "value1", param2 = "value2" }` |

### **App Service Plan Variables**

| Name | Description | Type | Required | Default | Example |
|------|-------------|------|----------|---------|:-------:|
| <a name="input_sku"></a>[sku](#input\_sku) | SKU block. | `object({ tier = string, size = string, capacity = optional(string) })` | No | `null` | See example below |
| <a name="input_app_service_plan_name"></a>[app_service_plan_name](#input\_app_service_plan_name) | The Name of the App Service Plan within which to create this Logic App. | `string` | No | `null` | `"my-app-service-plan"` |
| <a name="input_app_service_plan_kind"></a>[app_service_plan_kind](#input\_app_service_plan_kind) | The ID of the App Service Plan within which to create this Logic App. | `string` | No | `"Windows"` | `"Linux"` |
| <a name="input_is_app_service_plan_reserved"></a>[is_app_service_plan_reserved](#input\_is_app_service_plan_reserved) | Whether the App Service Plan is reserved. | `bool` | No | `true` | `false` |

## **Example Usage**

```hcl
module "logic_app" {
  source                        = "tfe.axisb.com/ax-tfe/logic-app/azurerm"
  version                       = "X.X.X"
  logic_app_name                = "my-logic-app"
  resource_group_name           = "my-resource-group"
  location                      = "East US"
  app_service_plan_id           = "app-service-plan-id"
  app_settings                  = {
    key1 = "value1"
    key2 = "value2"
  }
  use_extension_bundle          = true
  bundle_version                = "[1.*, 2.0.0)"
  connection_string             = {
    name  = "connection-string-name"
    type  = "SQLServer"
    value = "connection-string-value"
  }
  client_affinity_enabled       = true
  client_certificate_mode       = "Required"
  enabled                       = true
  https_only                    = true
  identity                      = {
    type         = "SystemAssigned"
    identity_ids = null
  }
  site_config                   = {
    always_on       = true
    app_scale_limit = 5
    cors = {
      allowed_origins     = ["*"]
      support_credentials = true
    }
    dotnet_framework_version = "v4.0"
    elastic_instance_minimum = 2
    ftps_state               = "Disabled"
    health_check_path        = "/"
    http2_enabled            = true
    ip_restriction = [
      {
        name                      = "ip-restriction-name"
        ip_address                = "0.0.0.0"
        virtual_network_subnet_id = null
        service_tag               = "Internet"
        priority                  = 100
        action                    = "Allow"
        headers = [
          {
            x_azure_fdid      = ["fdid1", "fdid2"]
            x_fd_health_probe = ["probe1", "probe2"]
            x_forwarded_for   = ["forward1", "forward2"]
            x_forwarded_host  = ["host1", "host2"]
          }
        ]
      }
    ]
    scm_ip_restriction = [
      {
        ip_address                = "0.0.0.0"
        service_tag               = "Internet"
        virtual_network_subnet_id = null
        name                      = "ip-restriction-name"
        priority                  = 100
        action                    = "Allow"
        headers = [
          {
            x_azure_fdid      = ["fdid1", "fdid2"]
            x_fd_health_probe = ["probe1", "probe2"]
            x_forwarded_for   = ["forward1", "forward2"]
            x_forwarded_host  = ["host1", "host2"]
          }
        ]
      }
    ]
  }
  storage_account_name          = "storage-account-name"
  storage_account_access_key    = "storage-account-access-key"
  storage_account_share_name    = "storage-account-share-name"
  logic_app_version             = "~3"
  virtual_network_subnet_id     = "virtual-network-subnet-id"
  tags                          = {
    environment = "dev"
  }

  # Workflow Parameters
  workflow_name                 = "my-workflow"
  access_control                = {
    action = {
      allowed_caller_ip_address_range = "0.0.0.0"
    }
    content = {
      allowed_caller_ip_address_range = "0.0.0.0"
    }
    trigger = {
      allowed_caller_ip_address_range = "0.0.0.0"
    }
    workflow_management = {
      allowed_caller_ip_address_range = "0.0.0.0"
    }
  }
  workflow_identity             = {
    type         = "SystemAssigned"
    identity_ids = null
  }
  integration_service_environment_id = "integration-service-id"
  logic_app_integration_account_id   = "integration-account-id"
  workflow_enabled              = true
  workflow_parameters           = {
    param1 = "value1"
    param2 = "value2"
  }
  workflow_schema               = "schema-definition"
  workflow_version              = "2.0.0.0"
  parameters                    = {
    param1 = "value1"
    param2 = "value2"
  }

  # App Service Plan
  sku                           = {
    tier     = "Standard"
    size     = "S1"
    capacity = null
  }
  app_service_plan_name         = "my-app-service-plan"
  app_service_plan_kind         = "Windows"
  is_app_service_plan_reserved  = true
}
