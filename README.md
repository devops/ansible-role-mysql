# Ansible Role: mysql

Install and configure MySQL or MariaDB server on RHEL/CentOS.

## Requirements


### Replication configuration

System Firewall must disabled or open mysql port default is 3306.

## Role Variables

### `defaults/main.yml`

* `mysql_root_username: root`
* `mysql_root_password: root`
* `mysql_character: ""`
* `mysql_port: 3306`
* `mysql_bind_address: 0.0.0.0`
* `mysql_datadir: "/var/lib/mysql"`
* `mysql_max_connections: "700"`
* `mysql_max_connect_errors: "1844674407370954751"`
* `mysql_key_buffer_size: "256M"`
* `mysql_max_allowed_packet: "1M"`
* `mysql_table_open_cache: "256"`
* `mysql_sort_buffer_size: "1M"`
* `mysql_read_buffer_size: "1M"`
* `mysql_read_rnd_buffer_size: "4M"`
* `mysql_myisam_sort_buffer_size: "64M"`
* `mysql_thread_cache_size: "8"`
* `mysql_query_cache_size: "16M"`
* `mysql_thread_concurrency: 8`
* `mysql_wait_timeout: "28800"`
* `mysql_log_bin: "mysql-bin"`
* `mysql_log_bin_index: "mysql-bin.index"`
* `mysql_binlog_format: "mixed"`
* `mysql_relay_log: "mysql-relay-bin"`
* `mysql_relay_log_index: "mysql-relay-bin.index"`
* `mysql_innodb_data_home_dir: "{{ mysql_datadir }}"`
* `mysql_innodb_data_file_path: "ibdata1:10M:autoextend"`
* `mysql_innodb_log_group_home_dir: "{{ mysql_datadir }}"`
* `mysql_innodb_buffer_pool_size: "2048M"`
* `mysql_innodb_additional_mem_pool_size: "20M"`
* `mysql_innodb_log_file_size: "512M"`
* `mysql_innodb_log_buffer_size: "8M"`
* `mysql_innodb_flush_log_at_trx_commit: "1"`
* `mysql_innodb_lock_wait_timeout: "50"`
* `mysql_innodb_extra: ""`
* `mysql_mysqldump_max_allowed_packet: "16M"`
* `mysql_myisamchk_key_buffer_size: "256M"`
* `mysql_myisamchk_sort_buffer_size: "256M"`
* `mysql_myisamchk_read_buffer: "2M"`
* `mysql_myisamchk_write_buffer: "2M"`
* `mysql_users: []`
* `mysql_replication_role: ""`
* `mysql_server_id: "1"`
* `mysql_slave_server_id: "2"`
* `mysql_replication_master: ""`
* `mysql_replication_user: []`
* `mysql_character: ""`
* `mysql_extra: ""`

### RedHat6 to see `vars/redhat-6.yml`

### RedHat7 to see `vars/redhat-7.yml`

## Dependencies

None.

## Example Playbook

    - name: Install MySQL server.
      hosts: mysql
      vars:
        mysql_root_username: root
        mysql_root_password: root
        mysql_users:
          - { name: "root", host: "%", password: "root", priv: "*.*:GRANT,ALL" }
        mysql_innodb_extra:
          innodb_rollback_on_timeout: 1
        mysql_datadir: "/data/mysql"
        mysql_character: "utf8"
        mysql_extra:
          log_bin_trust_function_creators: 1
      roles:
        - ansible-role-mysql

## Author Information

z
