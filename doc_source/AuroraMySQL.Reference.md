# Amazon Aurora MySQL Reference<a name="AuroraMySQL.Reference"></a>

This reference includes information about Aurora MySQL parameters and status variables\.

**Topics**
+ [Aurora MySQL Parameters](#AuroraMySQL.Reference.ParameterGroups)
+ [Inapplicable MySQL Parameters and Status Variables](#AuroraMySQL.Reference.Parameters.Inapplicable)
+ [Aurora MySQL Events](#AuroraMySQL.Reference.Waitevents)
+ [Aurora MySQL Stored Procedures](#AuroraMySQL.Reference.StoredProcs)

## Aurora MySQL Parameters<a name="AuroraMySQL.Reference.ParameterGroups"></a>

You manage your Amazon Aurora MySQL DB cluster in the same way that you manage other Amazon RDS DB instances, by using parameters in a DB parameter group\. Amazon Aurora differs from other DB engines in that you have a DB cluster that contains multiple DB instances\. As a result, some of the parameters that you use to manage your Aurora MySQL DB cluster apply to the entire cluster\. Other parameters apply only to a particular DB instance in the DB cluster\.

To manage cluster\-level parameters, you use DB cluster parameter groups\. To manage instance\-level parameters, you use DB parameter groups\. Each DB instance in an Aurora MySQL DB cluster is compatible with the MySQL database engine\. However, you apply some of the MySQL database engine parameters at the cluster level, and you manage these parameters using DB cluster parameter groups\. You can't find cluster\-level parameters in the DB parameter group for an instance in an Aurora DB cluster\. A list of cluster\-level parameters appears later in this topic\.

You can manage both cluster\-level and instance\-level parameters using the AWS Management Console, the AWS CLI, or the Amazon RDS API\. You use separate commands for managing cluster\-level parameters and instance\-level parameters\. For example, you can use the [modify\-db\-cluster\-parameter\-group](https://docs.aws.amazon.com/cli/latest/reference/rds/modify-db-cluster-parameter-group.html) CLI command to manage cluster\-level parameters in a DB cluster parameter group\. You can use the [modify\-db\-parameter\-group](https://docs.aws.amazon.com/cli/latest/reference/rds/modify-db-parameter-group.html) CLI command to manage instance\-level parameters in a DB parameter group for a DB instance in a DB cluster\.

You can view both cluster\-level and instance\-level parameters in the console, or by using the CLI or RDS API\. For example, you can use the [describe\-db\-cluster\-parameters](https://docs.aws.amazon.com/cli/latest/reference/rds/describe-db-cluster-parameters.html) AWS CLI command to view cluster\-level parameters in a DB cluster parameter group\. You can use the [describe\-db\-parameters](https://docs.aws.amazon.com/cli/latest/reference/rds/describe-db-parameters.html) CLI command to view instance\-level parameters in a DB parameter group for a DB instance in a DB cluster\.

For more information on DB parameter groups, see [Working with DB Parameter Groups and DB Cluster Parameter Groups](USER_WorkingWithParamGroups.md)\. For rules and restrictions for Aurora Serverless clusters, see [Aurora Serverless and Parameter Groups](aurora-serverless.how-it-works.md#aurora-serverless.parameter-groups)\.

**Topics**
+ [Cluster\-Level Parameters](#AuroraMySQL.Reference.Parameters.Cluster)
+ [Instance\-Level Parameters](#AuroraMySQL.Reference.Parameters.Instance)

### Cluster\-Level Parameters<a name="AuroraMySQL.Reference.Parameters.Cluster"></a>

The following table shows all of the parameters that apply to the entire Aurora MySQL DB cluster\. 


| Parameter name | Modifiable | Notes | 
| --- | --- | --- | 
|  `aurora_enable_replica_log_compression`  |  Yes  |   Doesn't apply to clusters that are part of an Aurora global database\.   | 
|  `aurora_enable_repl_bin_log_filtering`  |  Yes  |   Doesn't apply to clusters that are part of an Aurora global database\.   | 
|  `aurora_enable_zdr`  |  Yes  |   For more information, see [High Availability Considerations for Amazon Aurora MySQL Replication](AuroraMySQL.Replication.md#AuroraMySQL.Replication.Availability)\.   | 
|  `aurora_load_from_s3_role`  |  Yes  |   For more information, see [Loading Data into an Amazon Aurora MySQL DB Cluster from Text Files in an Amazon S3 Bucket](AuroraMySQL.Integrating.LoadFromS3.md)\.   | 
|  `aurora_select_into_s3_role`  |  Yes  |   For more information, see [Saving Data from an Amazon Aurora MySQL DB Cluster into Text Files in an Amazon S3 Bucket](AuroraMySQL.Integrating.SaveIntoS3.md)\.   | 
|  `auto_increment_increment`  |  Yes  |  | 
|  `auto_increment_offset`  |  Yes  |  | 
|  `aws_default_lambda_role`  |  Yes  |   For more information, see [Invoking a Lambda Function from an Amazon Aurora MySQL DB Cluster](AuroraMySQL.Integrating.Lambda.md)\.   | 
|  `aws_default_s3_role`  |  Yes  |  | 
|  `binlog_checksum`  |  Yes  |  | 
|  `binlog_format`  |  Yes  |  | 
|  `binlog_row_image`  |  No  |  | 
|  `binlog_rows_query_log_events`  |  No  |  | 
|  `character-set-client-handshake`  |  Yes  |  | 
|  `character_set_client`  |  Yes  |  | 
|  `character_set_connection`  |  Yes  |  | 
|  `character_set_database`  |  Yes  |  | 
|  `character_set_filesystem`  |  Yes  |  | 
|  `character_set_results`  |  Yes  |  | 
|  `character_set_server`  |  Yes  |  | 
|  `collation_connection`  |  Yes  |  | 
|  `collation_server`  |  Yes  |  | 
|  `completion_type`  |  Yes  |  | 
|  `default_storage_engine`  |  No  |   Aurora MySQL clusters use the InnoDB storage engine for all of your data\.   | 
|  `innodb_autoinc_lock_mode`  |  Yes  |  | 
|  `innodb_checksums`  |  No  |  | 
|  `innodb_cmp_per_index_enabled`  |  Yes  |  | 
|  `innodb_commit_concurrency`  |  Yes  |  | 
|  `innodb_data_home_dir`  |  No  | Aurora MySQL uses managed instances where you don't access the filesystem directly\. | 
|  `innodb_file_per_table`  |  Yes  |  | 
|  `innodb_flush_log_at_trx_commit`  |  Yes  |  | 
|  `innodb_ft_max_token_size`  |  Yes  |  | 
|  `innodb_ft_min_token_size`  |  Yes  |  | 
|  `innodb_ft_num_word_optimize`  |  Yes  |  | 
|  `innodb_ft_sort_pll_degree`  |  Yes  |  | 
|  `innodb_online_alter_log_max_size`  |  Yes  |  | 
|  `innodb_optimize_fulltext_only`  |  Yes  |  | 
|  `innodb_page_size`  |  No  |  | 
|  `innodb_purge_batch_size`  |  Yes  |  | 
|  `innodb_purge_threads`  |  Yes  |  | 
|  `innodb_rollback_on_timeout`  |  Yes  |  | 
|  `innodb_rollback_segments`  |  Yes  |  | 
|  `innodb_spin_wait_delay`  |  Yes  |  | 
|  `innodb_strict_mode`  |  Yes  |  | 
|  `innodb_support_xa`  |  Yes  |  | 
|  `innodb_sync_array_size`  |  Yes  |  | 
|  `innodb_sync_spin_loops`  |  Yes  |  | 
|  `innodb_table_locks`  |  Yes  |  | 
|  `innodb_undo_directory`  |  No  | Aurora MySQL uses managed instances where you don't access the filesystem directly\. | 
|  `innodb_undo_logs`  |  Yes  |  | 
|  `innodb_undo_tablespaces`  |  No  |  | 
|  `lc_time_names`  |  Yes  |  | 
|  `lower_case_table_names`  |  Yes  |  | 
|  `master-info-repository`  |  Yes  |  | 
|  `master_verify_checksum`  |  Yes  |  | 
|  `server_audit_events`  |  Yes  |  | 
|  `server_audit_excl_users`  |  Yes  |  | 
|  `server_audit_incl_users`  |  Yes  |  | 
|  `server_audit_logging`  |  Yes  | For instructions on uploading the logs to CloudWatch Logs, see [Publishing Amazon Aurora MySQL Logs to Amazon CloudWatch Logs](AuroraMySQL.Integrating.CloudWatch.md)\. | 
|  `server_id`  |  No  |  | 
|  `skip-character-set-client-handshake`  |  Yes  |  | 
|  `skip_name_resolve`  |  No  |  | 
|  `sync_frm`  |  Yes  |  | 
|  `time_zone`  |  Yes  |  | 

### Instance\-Level Parameters<a name="AuroraMySQL.Reference.Parameters.Instance"></a>

The following table shows all of the parameters that apply to a specific DB instance in an Aurora MySQL DB cluster\. 


| Parameter name | Modifiable | Notes | 
| --- | --- | --- | 
| `allow-suspicious-udfs` | No |  | 
| `aurora_lab_mode` | Yes |   For more information, see [Amazon Aurora MySQL Lab Mode](AuroraMySQL.Updates.LabMode.md)\.   | 
|  `aurora_oom_response`  |  Yes  |   For more information, see [ Amazon Aurora MySQL Out of Memory Issues ](CHAP_Troubleshooting.md#CHAP_Troubleshooting.AuroraMySQLOOM)\.   | 
| `autocommit` | Yes |  | 
| `automatic_sp_privileges` | Yes |  | 
| `back_log` | Yes |  | 
| `basedir` | No | Aurora MySQL uses managed instances where you don't access the filesystem directly\. | 
| `binlog_cache_size` | Yes |  | 
| `binlog_max_flush_queue_time` | Yes |  | 
| `binlog_order_commits` | Yes |  | 
| `binlog_stmt_cache_size` | Yes |  | 
| `bulk_insert_buffer_size` | Yes |  | 
| `concurrent_insert` | Yes |  | 
| `connect_timeout` | Yes |  | 
| `core-file` | No | Aurora MySQL uses managed instances where you don't access the filesystem directly\. | 
| `datadir` | No | Aurora MySQL uses managed instances where you don't access the filesystem directly\. | 
| `default_time_zone` | No |  | 
| `default_tmp_storage_engine` | Yes |  | 
| `default_week_format` | Yes |  | 
| `delay_key_write` | Yes |  | 
| `delayed_insert_limit` | Yes |  | 
| `delayed_insert_timeout` | Yes |  | 
| `delayed_queue_size` | Yes |  | 
| `div_precision_increment` | Yes |  | 
| `end_markers_in_json` | Yes |  | 
| `enforce_gtid_consistency` | Sometimes | Modifiable in Aurora MySQL version 2\.04 and later\. | 
| `eq_range_index_dive_limit` | Yes |  | 
| `event_scheduler` | Yes |  | 
| `explicit_defaults_for_timestamp` | Yes |  | 
| `flush` | No |  | 
| `flush_time` | Yes |  | 
| `ft_boolean_syntax` | No |  | 
| `ft_max_word_len` | Yes |  | 
| `ft_min_word_len` | Yes |  | 
| `ft_query_expansion_limit` | Yes |  | 
| `ft_stopword_file` | Yes |  | 
| `general_log` | Yes | For instructions on uploading the logs to CloudWatch Logs, see [Publishing Amazon Aurora MySQL Logs to Amazon CloudWatch Logs](AuroraMySQL.Integrating.CloudWatch.md)\. | 
| `general_log_file` | No | Aurora MySQL uses managed instances where you don't access the filesystem directly\. | 
| `group_concat_max_len` | Yes |  | 
| `gtid-mode` | Sometimes | Modifiable in Aurora MySQL version 2\.04 and later\. | 
| `host_cache_size` | Yes |  | 
| `init_connect` | Yes |  | 
| `innodb_adaptive_hash_index` | Yes |  | 
| `innodb_adaptive_max_sleep_delay` | Yes |  | 
| `innodb_autoextend_increment` | Yes |  | 
| `innodb_buffer_pool_dump_at_shutdown` | No |  | 
| `innodb_buffer_pool_dump_now` | No |  | 
| `innodb_buffer_pool_filename` | No |  | 
| `innodb_buffer_pool_load_abort` | No |  | 
| `innodb_buffer_pool_load_at_startup` | No |  | 
| `innodb_buffer_pool_load_now` | No |  | 
| `innodb_buffer_pool_size` | Yes |  | 
| `innodb_change_buffer_max_size` | No | Aurora MySQL doesn't use the InnoDB change buffer at all\. | 
| `innodb_compression_failure_threshold_pct` | Yes |  | 
| `innodb_compression_level` | Yes |  | 
| `innodb_compression_pad_pct_max` | Yes |  | 
| `innodb_concurrency_tickets` | Yes |  | 
| `innodb_file_format` | Yes |  | 
| `innodb_flush_log_at_timeout` | No |  | 
| `innodb_flushing_avg_loops` | No |  | 
| `innodb_force_load_corrupted` | No |  | 
| `innodb_ft_aux_table` | Yes |  | 
| `innodb_ft_cache_size` | Yes |  | 
| `innodb_ft_enable_stopword` | Yes |  | 
| `innodb_ft_server_stopword_table` | Yes |  | 
| `innodb_ft_user_stopword_table` | Yes |  | 
| `innodb_large_prefix` | Yes |  | 
| `innodb_lock_wait_timeout` | Yes |  | 
| `innodb_log_compressed_pages` | No |  | 
| `innodb_lru_scan_depth` | Yes |  | 
| `innodb_max_purge_lag` | Yes |  | 
| `innodb_max_purge_lag_delay` | Yes |  | 
| `innodb_monitor_disable` | Yes |  | 
| `innodb_monitor_enable` | Yes |  | 
| `innodb_monitor_reset` | Yes |  | 
| `innodb_monitor_reset_all` | Yes |  | 
| `innodb_old_blocks_pct` | Yes |  | 
| `innodb_old_blocks_time` | Yes |  | 
| `innodb_open_files` | Yes |  | 
| `innodb_print_all_deadlocks` | Yes |  | 
| `innodb_random_read_ahead` | Yes |  | 
| `innodb_read_ahead_threshold` | Yes |  | 
| `innodb_read_io_threads` | No |  | 
| `innodb_read_only` | No |   Aurora MySQL manages the read\-only and read\-write state of DB instances based on the type of cluster\. For example, a provisioned cluster has one read\-write DB instance \(the *primary instance*\) and any other instances in the cluster are read\-only \(the Aurora Replicas\)\.   | 
| `innodb_replication_delay` | Yes |  | 
| `innodb_sort_buffer_size` | Yes |  | 
| `innodb_stats_auto_recalc` | Yes |  | 
| `innodb_stats_method` | Yes |  | 
| `innodb_stats_on_metadata` | Yes |  | 
| `innodb_stats_persistent` | Yes |  | 
| `innodb_stats_persistent_sample_pages` | Yes |  | 
| `innodb_stats_transient_sample_pages` | Yes |  | 
| `innodb_thread_concurrency` | No |  | 
| `innodb_thread_sleep_delay` | Yes |  | 
| `interactive_timeout` | Yes |  | 
| `join_buffer_size` | Yes |  | 
| `keep_files_on_create` | Yes |  | 
| `key_buffer_size` | Yes |  | 
| `key_cache_age_threshold` | Yes |  | 
| `key_cache_block_size` | Yes |  | 
| `key_cache_division_limit` | Yes |  | 
| `local_infile` | Yes |  | 
| `lock_wait_timeout` | Yes |  | 
| `log-bin` | No |  | 
| `log_bin_trust_function_creators` | Yes |  | 
| `log_bin_use_v1_row_events` | Yes |  | 
| `log_error` | No |  | 
| `log_output` | Yes |  | 
| `log_queries_not_using_indexes` | Yes |  | 
| `log_slave_updates` | No |  | 
| `log_throttle_queries_not_using_indexes` | Yes |  | 
| `log_warnings` | Yes |  | 
| `long_query_time` | Yes |  | 
| `low_priority_updates` | Yes |  | 
| `max_allowed_packet` | Yes |  | 
| `max_binlog_cache_size` | Yes |  | 
| `max_binlog_size` | No |  | 
| `max_binlog_stmt_cache_size` | Yes |  | 
| `max_connect_errors` | Yes |  | 
| `max_connections` | Yes |   For more information, see [Maximum Connections to an Aurora MySQL DB Instance](AuroraMySQL.Managing.Performance.md#AuroraMySQL.Managing.MaxConnections)\.   | 
| `max_delayed_threads` | Yes |  | 
| `max_error_count` | Yes |  | 
| `max_heap_table_size` | Yes |  | 
| `max_insert_delayed_threads` | Yes |  | 
| `max_join_size` | Yes |  | 
| `max_length_for_sort_data` | Yes |  | 
| `max_prepared_stmt_count` | Yes |  | 
| `max_seeks_for_key` | Yes |  | 
| `max_sort_length` | Yes |  | 
| `max_sp_recursion_depth` | Yes |  | 
| `max_tmp_tables` | Yes |  | 
| `max_user_connections` | Yes |  | 
| `max_write_lock_count` | Yes |  | 
| `metadata_locks_cache_size` | Yes |  | 
| `min_examined_row_limit` | Yes |  | 
| `myisam_data_pointer_size` | Yes |  | 
| `myisam_max_sort_file_size` | Yes |  | 
| `myisam_mmap_size` | Yes |  | 
| `myisam_sort_buffer_size` | Yes |  | 
| `myisam_stats_method` | Yes |  | 
| `myisam_use_mmap` | Yes |  | 
| `net_buffer_length` | Yes |  | 
| `net_read_timeout` | Yes |  | 
| `net_retry_count` | Yes |  | 
| `net_write_timeout` | Yes |  | 
| `old-style-user-limits` | Yes |  | 
| `old_passwords` | Yes |  | 
| `optimizer_prune_level` | Yes |  | 
| `optimizer_search_depth` | Yes |  | 
| `optimizer_switch` | Yes |  | 
| `optimizer_trace` | Yes |  | 
| `optimizer_trace_features` | Yes |  | 
| `optimizer_trace_limit` | Yes |  | 
| `optimizer_trace_max_mem_size` | Yes |  | 
| `optimizer_trace_offset` | Yes |  | 
| `performance_schema` | Yes |  | 
| `pid_file` | No |  | 
| `plugin_dir` | No | Aurora MySQL uses managed instances where you don't access the filesystem directly\. | 
| `port` | No | Aurora MySQL manages the connection properties and enforces consistent settings for all DB instances in a cluster\. | 
| `preload_buffer_size` | Yes |  | 
| `profiling_history_size` | Yes |  | 
| `query_alloc_block_size` | Yes |  | 
| `query_cache_limit` | Yes |  | 
| `query_cache_min_res_unit` | Yes |  | 
| `query_cache_size` | Yes |  | 
| `query_cache_type` | Yes |  | 
| `query_cache_wlock_invalidate` | Yes |  | 
| `query_prealloc_size` | Yes |  | 
| `range_alloc_block_size` | Yes |  | 
| `read_buffer_size` | Yes |  | 
| `read_only` | No |   Aurora MySQL manages the read\-only and read\-write state of DB instances based on the type of cluster\. For example, a provisioned cluster has one read\-write DB instance \(the *primary instance*\) and any other instances in the cluster are read\-only \(the Aurora Replicas\)\.   | 
| `read_rnd_buffer_size` | Yes |  | 
| `relay-log` | No |  | 
| `relay_log_info_repository` | Yes |  | 
| `relay_log_recovery` | No |  | 
| `safe-user-create` | Yes |  | 
| `secure_auth` | Yes |  | 
| `secure_file_priv` | No | Aurora MySQL uses managed instances where you don't access the filesystem directly\. | 
| `skip-slave-start` | No |  | 
| `skip_external_locking` | No |  | 
| `skip_show_database` | Yes |  | 
| `slave_checkpoint_group` | Yes |  | 
| `slave_checkpoint_period` | Yes |  | 
| `slave_parallel_workers` | Yes |  | 
| `slave_pending_jobs_size_max` | Yes |  | 
| `slave_sql_verify_checksum` | Yes |  | 
| `slow_launch_time` | Yes |  | 
| `slow_query_log` | Yes | For instructions on uploading the logs to CloudWatch Logs, see [Publishing Amazon Aurora MySQL Logs to Amazon CloudWatch Logs](AuroraMySQL.Integrating.CloudWatch.md)\. | 
| `slow_query_log_file` | No | Aurora MySQL uses managed instances where you don't access the filesystem directly\. | 
| `socket` | No |  | 
| `sort_buffer_size` | Yes |  | 
| `sql_mode` | Yes |  | 
| `sql_select_limit` | Yes |  | 
| `stored_program_cache` | Yes |  | 
| `sync_binlog` | No |  | 
| `sync_master_info` | Yes |  | 
| `sync_relay_log` | Yes |  | 
| `sync_relay_log_info` | Yes |  | 
| `sysdate-is-now` | Yes |  | 
| `table_cache_element_entry_ttl` | No |  | 
| `table_definition_cache` | Yes |  | 
| `table_open_cache` | Yes |  | 
| `table_open_cache_instances` | Yes |  | 
| `temp-pool` | Yes |  | 
| `thread_handling` | No |  | 
| `thread_stack` | Yes |  | 
| `timed_mutexes` | Yes |  | 
| `tmp_table_size` | Yes |  | 
| `tmpdir` | No | Aurora MySQL uses managed instances where you don't access the filesystem directly\. | 
| `transaction_alloc_block_size` | Yes |  | 
| `transaction_prealloc_size` | Yes |  | 
| `tx_isolation` | Yes |  | 
| `updatable_views_with_limit` | Yes |  | 
| `validate-password` | No |  | 
| `validate_password_dictionary_file` | No |  | 
| `validate_password_length` | No |  | 
| `validate_password_mixed_case_count` | No |  | 
| `validate_password_number_count` | No |  | 
| `validate_password_policy` | No |  | 
| `validate_password_special_char_count` | No |  | 
| `wait_timeout` | Yes |  | 

## Inapplicable MySQL Parameters and Status Variables<a name="AuroraMySQL.Reference.Parameters.Inapplicable"></a>

Because of architectural differences between Aurora MySQL and MySQL, some MySQL parameters and status variables do not apply to Aurora MySQL\.

The following MySQL parameters do not apply to Aurora MySQL:
+ `innodb_adaptive_flushing`
+ `innodb_adaptive_flushing_lwm`
+ `innodb_change_buffering`
+ `innodb_checksum_algorithm`
+ `innodb_doublewrite`
+ `innodb_flush_method`
+ `innodb_flush_neighbors`
+ `innodb_io_capacity`
+ `innodb_io_capacity_max`
+ `innodb_log_buffer_size`
+ `innodb_log_file_size`
+ `innodb_log_files_in_group`
+ `innodb_max_dirty_pages_pct`
+ `innodb_use_native_aio`
+ `innodb_write_io_threads`
+ `thread_cache_size`

The following MySQL status variables do not apply to Aurora MySQL:
+ `innodb_buffer_pool_bytes_dirty`
+ `innodb_buffer_pool_pages_dirty`
+ `innodb_buffer_pool_pages_flushed`

**Note**  
These lists are not exhaustive\.

## Aurora MySQL Events<a name="AuroraMySQL.Reference.Waitevents"></a>

The following are some common wait events for Aurora MySQL\.

**Note**  
For information about the naming conventions used in MySQL wait events, see [ Performance Schema Instrument Naming Conventions](https://dev.mysql.com/doc/refman/5.6/en/performance-schema-instrument-naming.html) in the MySQL documentation\.

**io/aurora\_redo\_log\_flush**  
In this wait event, a session is writing data to Aurora storage\. Typically, this wait event is for a write I/O operation in Aurora MySQL\.

**io/aurora\_respond\_to\_client**  
In this wait event, a thread is in the process of returning the result set to the client\.

**io/file/csv/data**  
In this wait event, there are threads writing to CSV tables\. Check your CSV table usage\. A typical cause of this event is setting log\_output on a table\.

**io/file/innodb/innodb\_data\_file**  
In this wait event, there are threads waiting on I/O operations to storage\. This event is more prevalent in I/O intensive workloads\. SQL statements showing a comparatively large proportion of this wait event might be running disk intensive queries\. Or they might be requesting data that can't be satisfied from the InnoDB buffer pool\. To find out, check your query plans and cache hit ratios\. For more information, see [ Buffering and Caching](https://dev.mysql.com/doc/refman/5.6/en/buffering-caching.html) in the MySQL documentation\.

**io/file/sql/binlog**  
In this wait event, there is a thread waiting on a binlog file that is being written to disk\.

**io/socket/sql/client\_connection**  
In this wait event, a thread is in the process of handling a new connection\.

**io/table/sql/handler**  
This is a table I/O wait event\. Typically, these types of events can be followed by a nested event such as a file I/O event\. For more information about 'atom' and 'molecule' events in the Performance Schema, see [ Performance Schema Atom and Molecule Events](https://dev.mysql.com/doc/refman/5.6/en/performance-schema-atom-molecule-events.html) in the MySQL documentation\.

**lock/table/sql/handler**  
This wait event is a table lock wait event handler\. For more information about 'atom' and 'molecule' events in the Performance Schema, see [ Performance Schema Atom and Molecule Events](https://dev.mysql.com/doc/refman/5.6/en/performance-schema-atom-molecule-events.html) in the MySQL documentation\.

**synch/cond/mysys/my\_thread\_var::suspend**  
In this wait event, threads are suspended when they are waiting on a condition\. For example, this event occurs when threads are waiting for table level lock\. We recommend that you investigate your workload to see what threads may be acquiring table locks on your database instance\. For more information about table locking in MySQL, see [Table Locking Issues](https://dev.mysql.com/doc/refman/5.6/en/table-locking.html) in the MySQL documentation\.

**synch/cond/sql/MDL\_context::COND\_wait\_status**  
In this wait event, there are threads waiting on a table metadata lock\. For more information, see [Optimizing Locking Operations](https://dev.mysql.com/doc/refman/5.6/en/locking-issues.html) in the MySQL documentation\.

**synch/cond/sql/MYSQL\_BIN\_LOG::COND\_done**  
In this wait event, there is a thread waiting on a binlog file that is being written to disk\. Binary logging contention can occur on databases with a very high change rate\.

**synch/mutex/innodb/aurora\_lock\_thread\_slot\_futex**  
In this wait event, there is a thread that is waiting on an InnoDB record lock\. If you see this event, check your database for conflicting workloads\. For more information, see [InnoDB Locking](https://dev.mysql.com/doc/refman/5.6/en/innodb-locking.html) in the MySQL documentation\.

**synch/mutex/innodb/buf\_pool\_mutex**  
In this wait event, a thread has acquired a lock on the InnoDB buffer pool\.

**synch/mutex/sql/LOCK\_open**  
In this wait event, LOCK\_open is being used to protect various objects in the data dictionary\. This wait event indicates there are threads waiting to acquire these locks\. Typically, this event is caused by data dictionary contention\.

**synch/mutex/sql/LOCK\_table\_cache**  
In this wait event, there are threads waiting to acquire a lock on a table cache instance\. For more information, see [How MySQL Opens and Closes Tables](https://dev.mysql.com/doc/refman/5.6/en/table-cache.html) in the MySQL documentation\.

**synch/mutex/sql/LOG**  
In this wait event, there are threads waiting on a log lock\. For example, a thread might wait for a lock to write to the slow query log file\.

**synch/mutex/sql/MYSQL\_BIN\_LOG::LOCK\_commit**  
In this wait event, there is a thread that is waiting to acquire a lock with the intention of committing to the binary log\. Binary logging contention can occur on databases with a very high change rate\. Depending on your version of MySQL, there are certain locks being used to protect the consistency and durability of the binary log\. In RDS MySQL, binary logs are used for replication and the automated backup process\. In Aurora MySQL, binary logs are not needed for native replication or backups\. They are disabled by default but can be enabled and used for external replication or change data capture\. For more information, see [The Binary Log](https://dev.mysql.com/doc/refman/5.6/en/binary-log.html) in the MySQL documentation\.

**synch/mutex/sql/MYSQL\_BIN\_LOG::LOCK\_log**  
In this wait event, threads are actively locking the binary log file\. Binary logging contention can occur on databases with a very high change rate\. Depending on your version of MySQL, there are certain locks being used to protect the consistency and durability of the binary log\.

**synch/rwlock/innodb/dict**  
In this wait event, there are threads waiting on an rwlock held on the InnoDB data dictionary\.

**synch/rwlock/innodb/dict sys RW lock**  
In this event, there are threads that are waiting on an rwlock held on the InnoDB data dictionary\.

**synch/rwlock/innodb/dict\_operation\_lock**  
In this wait event, there are threads holding locks on InnoDB data dictionary operations\.

## Aurora MySQL Stored Procedures<a name="AuroraMySQL.Reference.StoredProcs"></a>

You can call the following stored procedures while connected to the primary instance in an Aurora MySQL cluster\. These procedures control how transactions are replicated from an external database into Aurora MySQL, or from Aurora MySQL to an external database\. To learn how to use replication based on global transaction identifiers \(GTIDs\) with Aurora MySQL, see [Using GTID\-Based Replication for Aurora MySQL](mysql-replication-gtid.md)\. 

**Topics**
+ [mysql\.rds\_set\_master\_auto\_position](#mysql_rds_set_master_auto_position)
+ [mysql\.rds\_set\_external\_master\_with\_auto\_position](#mysql_rds_set_external_master_with_auto_position)
+ [mysql\.rds\_skip\_transaction\_with\_gtid](#mysql_rds_skip_transaction_with_gtid)

### mysql\.rds\_set\_master\_auto\_position<a name="mysql_rds_set_master_auto_position"></a>

Sets the replication mode to be based on either binary log file positions or on global transaction identifiers \(GTIDs\)\.

#### Syntax<a name="mysql_rds_set_master_auto_position-syntax"></a>

```
CALL mysql.rds_set_master_auto_position (auto_position_mode);
```

#### Parameters<a name="mysql_rds_set_master_auto_position-parameters"></a>

 *auto\_position\_mode*   
A value that indicates whether to use log file position replication or GTID\-based replication:  
+ `0` – Use the replication method based on binary log file position\. The default is `0`\.
+ `1` – Use the GTID\-based replication method\.

#### Usage Notes<a name="mysql_rds_set_master_auto_position-usage-notes"></a>

 For an Aurora MySQL DB cluster, you call this stored procedure while connected to the primary instance\. 

The master user must run the `mysql.rds_set_master_auto_position` procedure\.

For Aurora, this procedure is supported for Aurora MySQL version 2\.04 and later MySQL 5\.7–compatible versions\. GTID\-based replication isn't supported for Aurora MySQL 1\.1 or 1\.0\.

### mysql\.rds\_set\_external\_master\_with\_auto\_position<a name="mysql_rds_set_external_master_with_auto_position"></a>

Configures an Aurora MySQL primary instance to accept incoming replication from an external MySQL instance\. This procedure also configures replication based on global transaction identifiers \(GTIDs\)\.

 This procedure is available for both Amazon RDS MySQL and Aurora MySQL\. It works differently depending on the context\. When used with Aurora MySQL, this procedure doesn't configure delayed replication\. This limitation is because Amazon RDS MySQL supports delayed replication but Aurora MySQL doesn't\. 

#### Syntax<a name="mysql_rds_set_external_master_with_auto_position-syntax"></a>

```
CALL mysql.rds_set_external_master_with_auto_position (
  host_name
  , host_port
  , replication_user_name
  , replication_user_password
  , ssl_encryption
);
```

#### Parameters<a name="mysql_rds_set_external_master_with_auto_position-parameters"></a>

 *host\_name*   
The host name or IP address of the MySQL instance running external to Aurora to become the replication master\.

 *host\_port*   
The port used by the MySQL instance running external to Aurora to be configured as the replication master\. If your network configuration includes Secure Shell \(SSH\) port replication that converts the port number, specify the port number that is exposed by SSH\.

 *replication\_user\_name*   
The ID of a user with `REPLICATION CLIENT` and `REPLICATION SLAVE` permissions on the MySQL instance running external to Aurora\. We recommend that you provide an account that is used solely for replication with the external instance\.

 *replication\_user\_password*   
The password of the user ID specified in `replication_user_name`\.

 *ssl\_encryption*   
This option is not currently implemented\.  The default is 0\.

#### Usage Notes<a name="mysql_rds_set_external_master_with_auto_position-usage-notes"></a>

 For an Aurora MySQL DB cluster, you call this stored procedure while connected to the primary instance\. 

The master user must run the `mysql.rds_set_external_master_with_auto_position` procedure\. The master user runs this procedure on the primary instance of an Aurora MySQL DB cluster that acts as a replication target\. This can be the replication target of an external MySQL DB instance or an Aurora MySQL DB cluster\.

For Aurora, this procedure is supported for Aurora MySQL version 2\.04 and later MySQL 5\.7\-compatible versions\. GTID\-based replication isn't supported for Aurora MySQL 1\.1 or 1\.0\.

Before you run `mysql.rds_set_external_master_with_auto_position`, configure the external MySQL DB instance to be a replication master\. To connect to the external MySQL instance, specify values for `replication_user_name` and `replication_user_password`\. These values must indicate a replication user that has `REPLICATION CLIENT` and `REPLICATION SLAVE` permissions on the external MySQL instance\. 

**To configure an external MySQL instance as a replication master**

1. Using the MySQL client of your choice, connect to the external MySQL instance and create a user account to be used for replication\. The following is an example\.

   ```
   CREATE USER 'repl_user'@'mydomain.com' IDENTIFIED BY 'SomePassW0rd'
   ```

1. On the external MySQL instance, grant `REPLICATION CLIENT` and `REPLICATION SLAVE` privileges to your replication user\. The following example grants `REPLICATION CLIENT` and `REPLICATION SLAVE` privileges on all databases for the `'repl_user'` user for your domain\.

   ```
   GRANT REPLICATION CLIENT, REPLICATION SLAVE ON *.* TO 'repl_user'@'mydomain.com'
   IDENTIFIED BY 'SomePassW0rd'
   ```

When you call `mysql.rds_set_external_master_with_auto_position`, Amazon RDS records certain information\. This information is the time, the user, and an action of `"set master"` in the `mysql.rds_history` and `mysql.rds_replication_status` tables\.

To skip a specific GTID\-based transaction that is known to cause a problem, you can use the [mysql\.rds\_skip\_transaction\_with\_gtid](#mysql_rds_skip_transaction_with_gtid) stored procedure\. For more information about working with GTID\-based replication, see [Using GTID\-Based Replication for Aurora MySQL](mysql-replication-gtid.md)\.

#### Examples<a name="mysql_rds_set_external_master_with_auto_position-examples"></a>

When run on an Aurora primary instance, the following example configures the Aurora cluster to act as a Read Replica of an instance of MySQL running external to Aurora\.

```
call mysql.rds_set_external_master_with_auto_position(
  'Externaldb.some.com',
  3306,
  'repl_user'@'mydomain.com',
  'SomePassW0rd');
```

### mysql\.rds\_skip\_transaction\_with\_gtid<a name="mysql_rds_skip_transaction_with_gtid"></a>

Skips replication of a transaction with the specified global transaction identifier \(GTID\) on an Aurora primary instance\.

You can use this procedure for disaster recovery when a specific GTID transaction is known to cause a problem\. Use this stored procedure to skip the problematic transaction\. Examples of problematic transactions include transactions that disable replication, delete important data, or cause the DB instance to become unavailable\.

#### Syntax<a name="mysql_rds_skip_transaction_with_gtid-syntax"></a>

```
CALL mysql.rds_skip_transaction_with_gtid (gtid_to_skip);
```

#### Parameters<a name="mysql_rds_skip_transaction_with_gtid-parameters"></a>

 *gtid\_to\_skip*   
The GTID of the replication transaction to skip\.

#### Usage Notes<a name="mysql_rds_skip_transaction_with_gtid-usage-notes"></a>

 For an Aurora MySQL DB cluster, you call this stored procedure while connected to the primary instance\. 

The master user must run the `mysql.rds_skip_transaction_with_gtid` procedure\.

For Aurora, this procedure is supported for Aurora MySQL version 2\.04 and later MySQL 5\.7\-compatible versions\. GTID\-based replication isn't supported for Aurora MySQL 1\.1 or 1\.0\.