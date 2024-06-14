# **Cosmos DB Module**

Terraform module to create Azure Cosmos DB accounts.

## **Description**

This module is used to create an Azure Cosmos DB account. It requires several attributes in order to be created on Azure, including `cosmos_account_name`, `resource_group_name`, `location`, `sku`, etc.

## **Variable Definitions**

| Name | Description | Type | Required | Default | Example |
|------|-------------|------|----------|---------|:-------:|
| <a name="input_cosmos_account_name"></a>[cosmos_account_name](#input\_cosmos_account_name) | The name of the CosmosDB account. | `string` | Yes | `""` | `"my-cosmos-account"` |
| <a name="input_existing_cosmosdb_accounnt_name"></a>[existing_cosmosdb_accounnt_name](#input\_existing_cosmosdb_accounnt_name) | The name of the Existing CosmosDB account. | `string` | No | `null` | `"existing-cosmos-account"` |
| <a name="input_offer_type"></a>[offer_type](#input\_offer_type) | The Offer Type for the CosmosDB account. | `string` | Yes | `""` | `"Standard"` |
| <a name="input_cosmos_api"></a>[cosmos_api](#input\_cosmos_api) | The Cosmos API for the CosmosDB account. | `string` | Yes | `""` | `"sql"` |
| <a name="input_resource_group_name"></a>[resource_group_name](#input\_resource_group_name) | The resource_group_name for the CosmosDB account should be created. | `string` | Yes | `""` | `"my-resource-group"` |
| <a name="input_location"></a>[location](#input\_location) | The Azure region where the CosmosDB account should be created. | `string` | Yes | `""` | `"East US"` |
| <a name="input_public_network_access_enabled"></a>[public_network_access_enabled](#input\_public_network_access_enabled) | Specifies whether public network access to the CosmosDB account is allowed. | `bool` | No | `false` | `true` |
| <a name="input_ip_firewall_enabled"></a>[ip_firewall_enabled](#input\_ip_firewall_enabled) | Specifies whether IP firewall rules should be enabled for the CosmosDB account. | `bool` | No | `false` | `true` |
| <a name="input_firewall_ips"></a>[firewall_ips](#input\_firewall_ips) | IP addresses or IP ranges to allow through the firewall. | `list(string)` | No | `null` | `["192.168.1.1", "192.168.1.2"]` |
| <a name="input_automatic_failover_enabled"></a>[automatic_failover_enabled](#input\_automatic_failover_enabled) | Enables automatic failover for the CosmosDB account. | `bool` | No | `false` | `true` |
| <a name="input_free_tier_enabled"></a>[free_tier_enabled](#input\_free_tier_enabled) | Enables the free tier for the CosmosDB account. | `bool` | No | `false` | `true` |
| <a name="input_multiple_write_locations_enabled"></a>[multiple_write_locations_enabled](#input\_multiple_write_locations_enabled) | Enables multi-region write for the CosmosDB account. | `bool` | No | `false` | `true` |
| <a name="input_key_vault_key_id"></a>[key_vault_key_id](#input\_key_vault_key_id) | The id of the Azure Key Vault for CosmosDB encryption keys. | `string` | No | `null` | `"key-vault-key-id"` |
| <a name="input_tags"></a>[tags](#input\_tags) | A map of tags to apply to the CosmosDB resources. | `map(string)` | No | `{}` | `{ environment = "dev" }` |
| <a name="input_consistency_level"></a>[consistency_level](#input\_consistency_level) | The consistency level for the CosmosDB account. | `string` | No | `"Session"` | `"Eventual"` |
| <a name="input_max_interval_in_seconds"></a>[max_interval_in_seconds](#input\_max_interval_in_seconds) | The maximum interval in seconds for session consistency. | `number` | No | `5` | `10` |
| <a name="input_max_staleness_prefix"></a>[max_staleness_prefix](#input\_max_staleness_prefix) | The maximum staleness prefix for session consistency. | `number` | No | `100` | `200` |
| <a name="input_capabilities"></a>[capabilities](#input\_capabilities) | A list of additional capabilities for the CosmosDB account. | `object({ name = string })` | No | `{}` | `{ name = "EnableGremlin" }` |
| <a name="input_default_identity_type"></a>[default_identity_type](#input\_default_identity_type) | Default Identity Type for the CosmosDB account. | `string` | No | `null` | `"SystemAssigned"` |
| <a name="input_identity_type"></a>[identity_type](#input\_identity_type) | Managed Identity Type for the CosmosDB account. | `string` | No | `null` | `"UserAssigned"` |
| <a name="input_identity_ids"></a>[identity_ids](#input\_identity_ids) | A list of User Assigned managed Identity IDs for the CosmosDB account. | `list(string)` | No | `null` | `["identity-id-1", "identity-id-2"]` |
| <a name="input_geo_locations"></a>[geo_locations](#input\_geo_locations) | A list of geo_locations for Cosmos DB. | `list(object({ location = string, failover_priority = number, zone_redundant = optional(bool) }))` | No | `[]` | `[{ location = "East US", failover_priority = 0 }]` |
| <a name="input_backup_enabled"></a>[backup_enabled](#input\_backup_enabled) | Enables backup for the CosmosDB account. | `bool` | No | `false` | `true` |
| <a name="input_backup_type"></a>[backup_type](#input\_backup_type) | The type of backup for the CosmosDB account. | `string` | No | `"Periodic"` | `"Continuous"` |
| <a name="input_backup_interval"></a>[backup_interval](#input\_backup_interval) | The backup interval in minutes for periodic backups. | `number` | No | `1440` | `60` |
| <a name="input_backup_retention"></a>[backup_retention](#input\_backup_retention) | The backup retention in hours for periodic backups. | `number` | No | `30` | `90` |
| <a name="input_analytical_storage"></a>[analytical_storage](#input\_analytical_storage) | Specifies whether analytical storage is enabled for the CosmosDB account. | `object({ enabled = bool, schema_type = string })` | No | `{ enabled = false, schema_type = "FullFidelity" }` | `{ enabled = true, schema_type = "Transactional" }` |
| <a name="input_enable_systemassigned_identity"></a>[enable_systemassigned_identity](#input\_enable_systemassigned_identity) | Enables a system-assigned identity for the CosmosDB account. | `bool` | No | `false` | `true` |
| <a name="input_enable_advanced_threat_protection"></a>[enable_advanced_threat_protection](#input\_enable_advanced_threat_protection) | Enables advanced threat protection for the CosmosDB account. | `bool` | No | `false` | `true` |
| <a name="input_virtual_network_rule"></a>[virtual_network_rule](#input\_virtual_network_rule) | A list of virtual network rules for the Cosmos DB account. | `list(object({ id = string, ignore_missing_vnet_service_endpoint = optional(bool) }))` | No | `null` | `[{ id = "vnet-id-1" }]` |
| <a name="input_cosmos_collection_name"></a>[cosmos_collection_name](#input\_cosmos_collection_name) | The name of the MongoDB collection. | `string` | No | `null` | `"my-collection"` |
| <a name="input_database_name"></a>[database_name](#input\_database_name) | The name of the MongoDB database where the collection will be created. | `string` | No | `null` | `"my-database"` |
| <a name="input_default_ttl_seconds"></a>[default_ttl_seconds](#input\_default_ttl_seconds) | The default TTL (Time to Live) in seconds for the MongoDB collection. | `number` | No | `null` | `86400` |
| <a name="input_analytical_storage_ttl"></a>[analytical_storage_ttl](#input\_analytical_storage_ttl) | The analytical storage TTL in seconds for the MongoDB collection. | `number` | No | `null` | `259200` |
| <a name="input_shard_key"></a>[shard_key](#input\_shard_key) | The shard key for the MongoDB collection. | `string` | No | `null` | `"my-shard-key"` |
| <a name="input_mongo_collection_max_throughput"></a>[mongo_collection_max_throughput](#input\_mongo_collection_max_throughput) | The autoscale settings max throughput (RU/s) for the MongoDB collection. | `number` | No | `null` | `4000` |
| <a name="input_mongo_collection_throughput"></a>[mongo_collection_throughput](#input\_mongo_collection_throughput) | The throughput (RU/s) for the MongoDB collection. | `number` | No | `null` | `2000` |
| <a name="input_indexes"></a>[indexes](#input\_indexes) | A list of MongoDB index configurations, including keys and uniqueness. | `list(object({ keys = list(string), unique = bool }))` | No | `null` | `[{ keys = ["key1", "key2"], unique = true }]` |
| <a name="input_mongo_database_name"></a>[mongo_database_name](#input\_mongo_database_name) | The name of the MongoDB database. | `string` | No | `null` | `"my-mongo-database"` |
| <a name="input_throughput"></a>[throughput](#input\_throughput) | The throughput (RU/s) for the MongoDB. | `number` | No | `null` | `4000` |
| <a name="input_max_throughput"></a>[max_throughput](#input\_max_throughput) | The maximum throughput (RU/s) for the MongoDB when using autoscaling. | `number` | No | `null` | `8000` |
| <a name="input_private_dns_zone_ids"></a>[private_dns_zone_ids](#input\_private_dns_zone_ids) | Private DNS Zone Ids. | `list(string)` | No | `[]` | `["zone-id-1", "zone-id-2"]` |
| <a name="input_subnet_id"></a>[subnet_id](#input\_subnet_id) | Subnet ids for private Cosmosdb. | `string` | No | `null` | `"subnet-id"` |
| <a name="input_privatednszonename"></a>[privatednszonename](#input\_privatednszonename) | Private DNS Zone Name for the Cosmosdb. | `string` | No | `null` | `"my-private-dns-zone"` |
| <a name="input_private_dns_zone_group"></a>[private_dns_zone_group](#input\_private_dns_zone_group) | Private DNS Zone Group details. | `list(object({ name = optional(string), private_dns_zone_ids = list(string) }))` | No | `[]` | `[ { name = "group-name", private_dns_zone_ids = ["zone-id-1", "zone-id-2"] } ]` |
| <a name="input_is_manual_connection"></a>[is_manual_connection](#input\_is_manual_connection) | Set Manual Connection. | `bool` | No | `false` | `true` |
| <a name="input_log_analytics_workspace_id"></a>[log_analytics_workspace_id](#input\_log_analytics_workspace_id) | Log Analytics Workspace Id. | `string` | Yes | `""` | `"workspace-id"` |
| <a name="input_assign_policy"></a>[assign_policy](#input\_assign_policy) | Enable policy for encryption set. | `bool` | No | `true` | `false` |
| <a name="input_is_virtual_network_filter_enabled"></a>[is_virtual_network_filter_enabled](#input\_is_virtual_network_filter_enabled) | Enable when virtual network rules are created. | `bool` | No | `true` | `false` |
| <a name="input_key_vault_id"></a>[key_vault_id](#input\_key_vault_id) | ID of the existing Key Vault. | `string` | No | `null` | `"key-vault-id"` |
| <a name="input_eventhub_name"></a>[eventhub_name](#input\_eventhub_name) | Name of Eventhub Name. | `string` | No | `null` | `"my-eventhub"` |
| <a name="input_key_permissions"></a>[key_permissions](#input\_key_permissions) | Permissions for encryption set. | `list(string)` | No | `["Get","WrapKey","UnwrapKey"]` | `["Get","WrapKey"]` |
| <a name="input_cassandra_cluster_service_principal_id"></a>[cassandra_cluster_service_principal_id](#input\_cassandra_cluster_service_principal_id) | Cassandra cluster service principal id. | `string` | No | `null` | `"service-principal-id"` |
| <a name="input_cassandra_keyspaces"></a>[cassandra_keyspaces](#input\_cassandra_keyspaces) | List of Cosmos DB Cassandra keyspaces to create. | `list(object({ keyspace_name = string, keyspace_throughput = number, keyspace_max_throughput = number }))` | No | `[]` | `[ { keyspace_name = "keyspace1", keyspace_throughput = 400, keyspace_max_throughput = 800 }]` |
| <a name="input_gremlin_dbs"></a>[gremlin_dbs](#input\_gremlin_dbs) | Map of Cosmos DB Gremlin DBs to create. | `list(object({ db_name = string, db_throughput = number, db_max_throughput = number }))` | No | `[]` | `[ { db_name = "gremlin-db", db_throughput = 400, db_max_throughput = 800 }]` |
| <a name="input_gremlin_graphs"></a>[gremlin_graphs](#input\_gremlin_graphs) | List of Cosmos DB Gremlin Graph to create. | `list(object({ graph_name = string, db_name = string, partition_key_path = string, partition_key_version = number, default_ttl_seconds = string, graph_throughput = number, graph_max_throughput = number, index_policy_settings = object({ indexing_automatic = bool, indexing_mode = string, included_paths = list(string), excluded_paths = list(string), composite_indexes = list(object({ indexes = set(object({ index_path = string, index_order = string })) })), spatial_indexes = list(object({ spatial_index_path = string })) }), conflict_resolution_policy = object({ mode = string, path = string, procedure = string }), unique_key = list(string) }))` | No | `[]` | `[ { graph_name = "graph1", db_name = "gremlin-db", partition_key_path = "/partitionKey", partition_key_version = 1, default_ttl_seconds = "P30D", graph_throughput = 400, graph_max_throughput = 800, index_policy_settings = { indexing_automatic = true, indexing_mode = "consistent", included_paths = ["/*"], excluded_paths = [], composite_indexes = [{ indexes = [{ index_path = "/path1", index_order = "ascending" }] }], spatial_indexes = [{ spatial_index_path = "/spatialIndex" }] }, conflict_resolution_policy = { mode = "LastWriterWins", path = "/path", procedure = "" }, unique_key = ["key1"] }]` |
| <a name="input_sql_dbs"></a>[sql_dbs](#input\_sql_dbs) | Map of Cosmos DB SQL DBs to create. | `list(object({ db_name = string, db_throughput = number, db_max_throughput = number }))` | No | `[]` | `[ { db_name = "sql-db", db_throughput = 400, db_max_throughput = 800 }]` |
| <a name="input_sql_db_containers"></a>[sql_db_containers](#input\_sql_db_containers) | List of Cosmos DB SQL Containers to create. | `list(object({ container_name = string, db_name = string, partition_key_path = string, partition_key_version = number, container_throughout = number, container_max_throughput = number, default_ttl = number, analytical_storage_ttl = number, indexing_policy_settings = object({ sql_indexing_mode = string, sql_included_path = string, sql_excluded_path = string, composite_indexes = list(object({ indexes = set(object({ path = string, order = string })) })), spatial_indexes = list(object({ path = string })) }), sql_unique_key = list(string), conflict_resolution_policy = object({ mode = string, path = string, procedure = string }) }))` | No | `[]` | `[ { container_name = "container1", db_name = "sql-db", partition_key_path = "/partitionKey", partition_key_version = 1, container_throughout = 400, container_max_throughput = 800, default_ttl = 3600, analytical_storage_ttl = 86400, indexing_policy_settings = { sql_indexing_mode = "consistent", sql_included_path = "/*", sql_excluded_path = "", composite_indexes = [{ indexes = [{ path = "/path", order = "ascending" }] }], spatial_indexes = [{ path = "/spatialIndex" }] }, sql_unique_key = ["key1"], conflict_resolution_policy = { mode = "LastWriterWins", path = "/path", procedure = "" } }]` |
| <a name="input_postgresql_firewall_rule_specification"></a>[postgresql_firewall_rule_specification](#input\_postgresql_firewall_rule_specification) | Postgresql Firewall Rule. | `list(object({ name = string, start_ip_address = string, end_ip_address = string }))` | No | `[]` | `[ { name = "rule1", start_ip_address = "192.168.1.1", end_ip_address = "192.168.1.254" }]` |
| <a name="input_postgresql_cluster_specification"></a>[postgresql_cluster_specification](#input\_postgresql_cluster_specification) | PostgreSQL cluster specification. | `list(object({ name = string, administrator_login_password = optional(string), coordinator_storage_quota_in_mb = optional(number), coordinator_vcore_count = optional(number), node_count = number, citus_version = optional(string), coordinator_public_ip_access_enabled = optional(bool), coordinator_server_edition = optional(string), ha_enabled = optional(bool), node_public_ip_access_enabled = optional(bool), node_server_edition = optional(string), node_storage_quota_in_mb = optional(number), node_vcores = optional(number), preferred_primary_zone = optional(string), shards_on_coordinator_enabled = optional(bool), sql_version = optional(string) }))` | No | `[]` | `[ { name = "cluster1", node_count = 3 }]` |

## **Example Usage**

```hcl
module "cosmos_db" {
  source                  = "tfe.axisb.com/ax-tfe/cosmosdb/azurerm"
  version                 = "X.X.X"
  cosmos_account_name     = "my-cosmos-account"
  offer_type              = "Standard"
  cosmos_api              = "Mongo"
  resource_group_name     = "my-resource-group"
  location                = "East US"
  public_network_access_enabled = false
  ip_firewall_enabled     = true
  firewall_ips            = ["192.168.1.1", "192.168.1.2"]
  automatic_failover_enabled = true
  free_tier_enabled       = false
  multiple_write_locations_enabled = false
  key_vault_key_id        = "key-vault-key-id"
  tags                    = { environment = "dev" }
  consistency_level       = "Eventual"
  max_interval_in_seconds = 10
  max_staleness_prefix    = 100
  capabilities            = { name = "EnableMongo" }
  default_identity_type   = "SystemAssigned"
  identity_type           = "SystemAssigned"
  identity_ids            = ["identity-id-1", "identity-id-2"]
  geo_locations           = [
    {
      location          = "West US"
      failover_priority = 0
    },
    {
      location          = "East US"
      failover_priority = 1
    }
  ]
  backup_enabled          = true
  backup_type             = "Continuous"
  backup_interval         = 30
  backup_retention        = 60
  analytical_storage      = {
    enabled     = true
    schema_type = "Transactional"
  }
  enable_systemassigned_identity = true
  enable_advanced_threat_protection = true
  virtual_network_rule    = [
    {
      id                                   = "subnet-id"
      ignore_missing_vnet_service_endpoint = false
    }
  ]
  collection_name         = "my-collection"
  database_name           = "my-database"
  default_ttl_seconds     = 3600
  analytical_storage_ttl  = 86400
  shard_key               = "/partitionKey"
  mongo_collection_max_throughput = 4000
  mongo_collection_throughput     = 2000
  indexes                 = [{ keys = ["key1", "key2"], unique = true }]
  mongo_database_name     = "my-mongo-database"
  throughput              = 4000
  max_throughput          = 8000
  private_dns_zone_ids    = ["zone-id-1", "zone-id-2"]
  privatednszonename      = "my-private-dns-zone"
  private_dns_zone_group  = [
    {
      name = "group-name"
      private_dns_zone_ids  = ["zone-id-1", "zone-id-2"]
    }
  ]
  is_manual_connection    = true
  log_analytics_workspace_id = "workspace-id"
  assign_policy           = false
  is_virtual_network_filter_enabled = false
  key_vault_id            = "key-vault-id"
  eventhub_name           = "my-eventhub"
  key_permissions         = ["Get", "WrapKey"]
  cassandra_cluster_service_principal_id = "service-principal-id"
  cassandra_keyspaces     = [
    {
      keyspace_name           = "keyspace1"
      keyspace_throughput     = 400
      keyspace_max_throughput = 800
    }
  ]
  gremlin_dbs             = [
    {
      db_name           = "gremlin-db"
      db_throughput     = 400
      db_max_throughput = 800
    }
  ]
  gremlin_graphs          = [
    {
      graph_name            = "graph1"
      db_name               = "gremlin-db"
      partition_key_path    = "/partitionKey"
      partition_key_version = 1
      default_ttl_seconds   = "P30D"
      graph_throughput      = 400
      graph_max_throughput  = 800
      index_policy_settings = {
        indexing_automatic  = true
        indexing_mode       = "consistent"
        included_paths      = ["/*"]
        excluded_paths      = []
        composite_indexes   = [{ indexes = [{ path = "/path1", order = "ascending" }] }]
        spatial_indexes     = [{ spatial_index_path = "/spatialIndex" }]
      }
      conflict_resolution_policy = {
        mode      = "LastWriterWins"
        path      = "/path"
        procedure = ""
      }
      unique_key = ["key1"]
    }
  ]
  sql_dbs                 = [
    {
      db_name           = "sql-db"
      db_throughput     = 400
      db_max_throughput = 800
    }
  ]
  sql_db_containers       = [
    {
      container_name           = "container1"
      db_name                  = "sql-db"
      partition_key_path       = "/partitionKey"
      partition_key_version    = 1
      container_throughout     = 400
      container_max_throughput = 800
      default_ttl              = 3600
      analytical_storage_ttl   = 86400
      indexing_policy_settings = {
        sql_indexing_mode = "consistent"
        sql_included_path = "/*"
        sql_excluded_path = ""
        composite_indexes = [{ indexes = [{ path = "/path", order = "ascending" }] }]
        spatial_indexes   = [{ path = "/spatialIndex" }]
      }
      sql_unique_key = ["key1"]
      conflict_resolution_policy = {
        mode      = "LastWriterWins"
        path      = "/path"
        procedure = ""
      }
    }
  ]
  postgresql_firewall_rule_specification = [
    {
      name             = "rule1"
      start_ip_address = "192.168.1.1"
      end_ip_address   = "192.168.1.254"
    }
  ]
  postgresql_cluster_specification = [
    {
      name                                 = "cluster1"
      administrator_login_password         = "H@Sh1CoR3!"
      coordinator_storage_quota_in_mb      = 131072
      coordinator_vcore_count              = 2
      node_count                           = 3
      citus_version                        = null
      coordinator_public_ip_access_enabled = true
      coordinator_server_edition           = "GeneralPurpose"
      ha_enabled                           = false
      node_public_ip_access_enabled        = false
      node_server_edition                  = "MemoryOptimized"
      node_storage_quota_in_mb             = 131072
      node_vcores                          = 4
      preferred_primary_zone               = "East US"
      shards_on_coordinator_enabled        = false
      sql_version                          = null
    }
  ]
}
