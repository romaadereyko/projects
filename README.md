<h1 align="center">This is diplom project of "TeachMeSkills" courses in group DOS-13-onl by romaadereyko!</h1>

---

# Installation

`tar -zxvf Diplom.tar.gz`
`cd Diplom`
`ansible-playbook playbook/diplom.yaml`

---

## Usage

### Global variables

Global variables stored in ./Diplom/inventory/group_vars/localhosts.yaml

```
registry_cont_name: registry
ansible_connection: local
ansible_ssh_private_key_file: ssh/localhost.priv
network_name: diplom
cont_start: --rm --name
timezone: Europe/Minsk
mem_res: "10G"
service_password: "SomeExtraStrongPassword"
service_user: "root"
service_timeout: "240"
```

### Local variables

Local variables stored in ./Diplom/roles/role_name/defaults/main.yml

```
---
# defaults file for elk
# Filebeat vars
file_cont_name: "filebeat"
file_image: "localhost:5000/filebeat"
#file_ports_src:
# - "list"
#file_ports_dest:
# - "list"
file_volumes_src:
 - "/srv/elk/filebeat_config/filebeat.yml"
 - "/var/lib/docker/containers"
 - "/var/run/docker.sock"
file_volumes_dest:
 - "/usr/share/filebeat/filebeat.yml"
 - "/var/lib/docker/containers:ro"
 - "/var/run/docker.sock:ro"
#file_environment:
# - "list"
file_root: "true"

# Logstash vars
log_cont_name: "logstash"
log_image: "localhost:5000/logstash"
#log_ports_src:
# - "list"
#log_ports_dest:
# - "list"
log_volumes_src:
 - "/srv/elk/logstash_pipelines"
log_volumes_dest:
 - "/usr/share/logstash/pipeline"
#log_environment:
# - "list"
#log_root:

# Elasticsearch vars
elk_cont_name: "elasticsearch"
elk_image: "localhost:5000/elk"
#elk_ports_src:
# - "list"
#elk_ports_dest:
# - "list"
elk_volumes_src:
 - "/srv/elk/elasticsearch_data"
elk_volumes_dest:
 - "/usr/share/elasticsearch/data"
elk_environment:
 - "discovery.type=single-node"
mem_res: "10G"
#elk_root:

# Kibana vars
kib_cont_name: "kibana"
kib_image: "localhost:5000/kibana"
#kib_ports_src:
# - "5601"
#kib_ports_dest:
# - "5601"
#kib_volumes_src:
# - "list"
#kib_volumes_dest:
# - "list"
kib_environment:
 - "elasticsearch.hosts=http://elasticsearch:9200"
#kib_root:
```

### Playbooks

Project has 3 global playbooks:
+ playbook/keys.yaml for setting up localhost
+ playbook/diplom.yaml for install project
+ playbook/diplom.yaml for cleaning old builds