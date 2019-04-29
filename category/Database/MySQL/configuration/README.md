# my.ini

```
mysqld --defaults-file="C:\Program Files\MySQL\MySQL Server X.Y\my.ini"
mysqld --install MySQLXY --defaults-file="C:\Program Files\MySQL\MySQL Server X.Y\my.ini"
net start MySQLXY
```



#### [client]

port=3306



#### [mysql]

no-beep=



#### [mysqld]

port=3306

datadir=D:/env/win/ProgramData/MySQL/MySQL Server 8.0/Data

default_authentication_plugin=mysql_native_password

default-storage-engine=INNODB

sql-mode="STRICT_TRANS_TABLES,NO_ENGINE_SUBSTITUTION"



> General and Slow logging.

log-output=FILE

general-log=0

general_log_file="END.log"

slow-query-log=1

slow_query_log_file="END-slow.log"

long_query_time=10



> Binary Logging.

log-bin="END-bin"

log-error="END.err"

server-id=1

lower_case_table_names=1

secure-file-priv="D:/env/win/ProgramData/MySQL/MySQL Server 8.0/Uploads"

max_connections=151

table_open_cache=2000

tmp_table_size=10M

thread_cache_size=10

myisam_max_sort_file_size=100G

myisam_sort_buffer_size=12M

key_buffer_size=8M

read_buffer_size=23K

read_rnd_buffer_size=256K



> INNODB Specific options

innodb_flush_log_at_trx_commit=1

innodb_log_buffer_size=1M

innodb_buffer_pool_size=8M

innodb_log_file_size=48M

innodb_thread_concurrency=9

innodb_autoextend_increment=64

innodb_buffer_pool_instances=8

innodb_concurrency_tickets=5000

innodb_old_blocks_time=1000

innodb_open_files=300

innodb_stats_on_metadata=0

innodb_file_per_table=1

innodb_checksum_algorithm=0



back_log=80

flush_time=0

join_buffer_size=256K

max_allowed_packet=4M

max_connect_errors=100

open_files_limit=4161

sort_buffer_size=256K

table_definition_cache=1400

binlog_row_event_max_size=8K

sync_master_info=10000

sync_relay_log=10000

sync_relay_log_info=10000

loose_mysqlx_port=33060

