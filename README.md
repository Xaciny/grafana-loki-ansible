# Общее описание

### Архитектура
1 Нода 
    Docker: Grafana + Postgres(мастер) + Loki 
    Нативно: Promtail 
2 Нода 
    Docker: Grafana + Postgre(standyц) + Loki
    Нативно: Promtail

### Стек
Ansible+docker+bash+nginx+pgsql

### Древо репозитория с пояснением

├── README.md
├── ansible.cfg - r
├── grafana.yml
├── inventory
│   ├── group_vars
│   │   └── grafana
│   │       └── grafana.yml
│   └── hosts.yml
└── roles
    └── grafana
        ├── tasks
        │   └── main.yml
        └── templates
            ├── certs
            ├── docker-compose.yml.j2
            ├── grafana
            │   └── provisioning
            │       └── datasources
            │           └──  loki.yaml
            ├── nginx
            │   └── http.d
            │       └── nginx.conf.j2
            └── psql
                └── init_sql.conf.j2