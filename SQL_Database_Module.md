# **SQL Database Module**

Terraform module to create Azure SQL Database.

# **Description**

This module is used to create an Azure SQL Database. It requires several attributes in order to be created on Azure, including `name`, `primary_server_id`, `secondary_server_id`, `sku_name`, `license_type`, etc.

# **Variable Definitions**

| Name | Description | Type | Required | Default | Example |
|------|-------------|------|----------|---------|:-------:|
| <a name="input_name"></a>[name](#input\_name) | The name of the SQL database. | `string` | Yes | `""` | `"my-sql-db"` |
| <a name="input_primary_server_id"></a>[primary_server_id](#input\_primary_server_id) | The ID of the SQL server where the database will be created. | `string` | Yes | `""` | `"primary-server-id"` |
| <a name="input_secondary_server_id"></a>[secondary_server_id](#input\_secondary_server_id) | The ID of the Secondary SQL server. | `string` | Yes | `""` | `"secondary-server-id"` |
| <a name="input_sku_name"></a>[sku_name](#input\_sku_name) | The SKU name for the database. | `string` | No | `null` | `"Basic"` |
| <a name="input_license_type"></a>[license_type](#input\_license_type) | The license type for the database. | `string` | No | `null` | `"LicenseIncluded"` |
| <a name="input_collation"></a>[collation](#input\_collation) | The collation for the database. | `string` | No | `null` | `"SQL_Latin1_General_CP1_CI_AS"` |
| <a name="input_max_size_gb"></a>[max_size_gb](#input\_max_size_gb) | The maximum size in GB for the database. | `number` | No | `null` | `10` |
| <a name="input_zone_redundant"></a>[zone_redundant](#input\_zone_redundant) | Indicates whether the database is zone redundant. | `bool` | No | `null` | `true` |
| <a name="input_min_capacity"></a>[min_capacity](#input\_min_capacity) | The minimum capacity for the database. | `number` | No | `null` | `0.5` |
| <a name="input_auto_pause_delay_in_minutes"></a>[auto_pause_delay_in_minutes](#input\_auto_pause_delay_in_minutes) | The delay in minutes before automatically pausing the database. | `number` | No | `null` | `60` |
| <a name="input_import"></a>[import](#input\_import) | The import block for the database. | `object` | No | `null` | `{ storage_uri = "uri", storage_key = "key", storage_key_type = "type", administrator_login = "admin", administrator_login_password = "password", authentication_type = "type", storage_account_id = "account_id" }` |
| <a name="input_read_scale"></a>[read_scale](#input\_read_scale) | Enable or disable read scale for the database. | `bool` | No | `null` | `true` |
| <a name="input_read_replica_count"></a>[read_replica_count](#input\_read_replica_count) | The number of read replicas for the database. | `number` | No | `null` | `3` |
| <a name="input_create_mode"></a>[create_mode](#input\_create_mode) | The mode used to create the database. | `string` | No | `null` | `"Default"` |
| <a name="input_creation_source_database_id"></a>[creation_source_database_id](#input\_creation_source_database_id) | The ID of the source database when create_mode requires it. | `string` | No | `null` | `"source-db-id"` |
| <a name="input_restore_point_in_time"></a>[restore_point_in_time](#input\_restore_point_in_time) | The restore point in time for PointInTimeRestore. | `string` | No | `null` | `"2022-01-01T00:00:00Z"` |
| <a name="input_recover_database_id"></a>[recover_database_id](#input\_recover_database_id) | The ID of the source database when create_mode is Recovery. | `string` | No | `null` | `"recover-db-id"` |
| <a name="input_restore_dropped_database_id"></a>[restore_dropped_database_id](#input\_restore_dropped_database_id) | The ID of the source database when create_mode is Restore. | `string` | No | `null` | `"restore-db-id"` |
| <a name="input_elastic_pool_id"></a>[elastic_pool_id](#input\_elastic_pool_id) | The ID of the elastic pool if the database is in an elastic pool. | `string` | No | `null` | `"pool-id"` |
| <a name="input_storage_account_type"></a>[storage_account_type](#input\_storage_account_type) | The storage account type for the database. | `string` | No | `null` | `"Standard_LRS"` |
| <a name="input_geo_backup_enabled"></a>[geo_backup_enabled](#input\_geo_backup_enabled) | Indicates whether geo-redundant backups are enabled for the database. | `bool` | No | `null` | `true` |
| <a name="input_maintenance_configuration_name"></a>[maintenance_configuration_name](#input\_maintenance_configuration_name) | The name of the maintenance configuration for the database. | `string` | No | `null` | `"maintenance-config"` |
| <a name="input_ledger_enabled"></a>[ledger_enabled](#input\_ledger_enabled) | Indicates whether ledger is enabled for the database. | `bool` | No | `false` | `true` |
| <a name="input_long_term_retention_policy"></a>[long_term_retention_policy](#input\_long_term_retention_policy) | Configuration for long-term retention policy. | `object` | No | `null` | `{ weekly_retention = 4, monthly_retention = 12, yearly_retention = 7, week_of_year = 5 }` |
| <a name="input_short_term_retention_policy"></a>[short_term_retention_policy](#input\_short_term_retention_policy) | Configuration for short-term retention policy. | `object` | No | `null` | `{ retention_days = 30, backup_interval_in_hours = 6 }` |
| <a name="input_threat_detection_policy"></a>[threat_detection_policy](#input\_threat_detection_policy) | Threat detection policy block. | `object` | No | `null` | `{ state = "Enabled", email_account_admins = "Enabled", email_addresses = ["admin@example.com"], retention_days = 30, disabled_alerts = ["SQL_Injection", "Access_Anomaly"], storage_endpoint = "endpoint", storage_account_access_key = "access_key" }` |
| <a name="input_tags"></a>[tags](#input\_tags) | Tags to apply to the SQL database. | `map(string)` | No | `{}` | `{ environment = "dev" }` |
| <a name="input_enabled_auditing_policy"></a>[enabled_auditing_policy](#input\_enabled_auditing_policy) | Whether enabled extended auditing. | `bool` | No | `false` | `true` |
| <a name="input_enabled"></a>[enabled](#input\_enabled) | Whether enabled extended auditing. | `bool` | No | `true` | `false` |
| <a name="input_log_monitoring_enabled"></a>[log_monitoring_enabled](#input\_log_monitoring_enabled) | Enabled auditing event to azure Monitor. | `bool` | No | `true` | `false` |
| <a name="input_storage_endpoint"></a>[storage_endpoint](#input\_storage_endpoint) | The blob storage endpoint. | `string` | No | `null` | `"blob.endpoint.com"` |
| <a name="input_retention_in_days"></a>[retention_in_days](#input\_retention_in_days) | The number of days to retain logs for in storage account. | `number` | No | `0` | `30` |
| <a name="input_storage_account_access_key"></a>[storage_account_access_key](#input\_storage_account_access_key) | The access key use for the auditing storage account. | `string` | No | `null` | `"access_key"` |
| <a name="input_storage_account_access_key_is_secondary"></a>[storage_account_access_key_is_secondary](#input\_storage_account_access_key_is_secondary) | The secondary access key use for the auditing storage account. | `string` | No | `null` | `"secondary_access_key"` |
| <a name="input_transparent_data_encryption_enabled"></a>[transparent_data_encryption_enabled](#input\_transparent_data_encryption_enabled) | Enabled Transparent data encryption. | `bool` | No | `true` | `false` |

## **Example Usage**

```hcl
module "sql_database" {
  source                           = "tfe.axisb.com/ax-tfe/sql-database/azurerm"
  version                          = "X.X.X"
  name                             = "my-sql-db"
  primary_server_id                = "primary-server-id"
  secondary_server_id              = "secondary-server-id"
  sku_name                         = "Basic"
  license_type                     = "LicenseIncluded"
  collation                        = "SQL_Latin1_General_CP1_CI_AS"
  max_size_gb                      = 10
  zone_redundant                   = true
  min_capacity                     = 0.5
  auto_pause_delay_in_minutes      = 60
  import = {
    storage_uri                 = "uri"
    storage_key                 = "key"
    storage_key_type            = "type"
    administrator_login         = "admin"
    administrator_login_password = "password"
    authentication_type         = "type"
    storage_account_id          = "account_id"
  }
  read_scale                      = true
  read_replica_count              = 3
  create_mode                     = "Default"
  creation_source_database_id     = "source-db-id"
  restore_point_in_time           = "2022-01-01T00:00:00Z"
  recover_database_id             = "recover-db-id"
  restore_dropped_database_id     = "restore-db-id"
  elastic_pool_id                 = "pool-id"
  storage_account_type            = "Standard_LRS"
  geo_backup_enabled              = true
  maintenance_configuration_name  = "maintenance-config"
  ledger_enabled                  = true
  long_term_retention_policy      = {
    weekly_retention  = 4
    monthly_retention = 12
    yearly_retention  = 7
    week_of_year      = 5
  }
  short_term_retention_policy     = {
    retention_days             = 30
    backup_interval_in_hours   = 6
  }
  threat_detection_policy         = {
    state                      = "Enabled"
    email_account_admins       = "Enabled"
    email_addresses            = ["admin@example.com"]
    retention_days             = 30
    disabled_alerts            = ["SQL_Injection", "Access_Anomaly"]
    storage_endpoint           = "endpoint"
    storage_account_access_key = "access_key"
  }
  tags                             = { environment = "dev" }
  enabled_auditing_policy          = true
  enabled                          = false
  log_monitoring_enabled           = true
  storage_endpoint                 = "blob.endpoint.com"
  retention_in_days                = 30
  storage_account_access_key       = "access_key"
  storage_account_access_key_is_secondary = "secondary_access_key"
  transparent_data_encryption_enabled = false
}
