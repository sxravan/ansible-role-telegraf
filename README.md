# Ansible Role: telegraf

Installs and configures the Telegraf agent for collecting and shipping metrics.

## Requirements

- Ansible ≥ 2.9
- Supported OS: Debian, Ubuntu, RHEL/CentOS/Rocky

## Role Variables

You **must** declare the following variables either in your playbook or in your inventory:

```yaml
telegraf_urls:
  - "URL1:PORT1"
telegraf_organization: "ORG1"
telegraf_bucket: "BUCKET1"
telegraf_precision: "s"
telegraf_input_systems_net_interfaces:
  - "lo"
  - "INT1"
```

The `vault_telegraf_token` (InfluxDB auth token) can be stored in an Ansible Vault file or set as an environment variable:

```bash
export vault_telegraf_token="YOUR_TOKEN"
```

## Example Playbook

```yaml
- hosts: all
  roles:
    - role: sxravan.ansible-role-telegraf
      vars:
        telegraf_urls:
          - "https://influxdb.example.com:8086"
        telegraf_organization: "my-org"
        telegraf_bucket: "metrics"
        telegraf_precision: "s"
        telegraf_input_systems_net_interfaces:
          - "lo"
          - "eth0"
        vault_telegraf_token: "YOUR_TOKEN"
```
