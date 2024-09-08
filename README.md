Role Name
=========

An Ansible role to manage Wordpress instances

Requirements
------------

- docker
- ansible

Role Variables
--------------

## Required variables
```yaml
site_working_directory: "/path"
db_image: "mariadb" #mysql or mariadb
db_version: 11
db_root_password: "supersecurepassword"
db_database: "wordpress"
db_user: "db_user"
db_user_password: "securepassword"
wp_router_traefik: "router_base_name"
wp_domains: "Host(`fqdn`) || Host(`www.fqdn`)"
```

## Optional variables
```yaml
traefik_tls_provider: "letsencrypt" #letsencrypt (HTTP-Challange) or cloudflare (DNS-Challange)
traefik_docker_network: "webproxy"
db_volume: "./data/db"
db_resources_limits:
  cpus: "0.5"
  memory: "300M"
db_logging:
  driver: "json-file"
  max_size: "1m"
  max_file: "10"
wp_image: "wordpress"
wp_version: "latest"
wp_resources_limits:
  cpus: "0.5"
  memory: "300M"
wp_volume: "./data/site"
wp_table_prefix: "wp_"
wp_logging:
  driver: "json-file"
  max_size: "1m"
  max_file: "10"
```

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: mfic.docker-wordpress }

License
-------

MIT