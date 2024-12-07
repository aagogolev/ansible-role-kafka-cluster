# Kafka Cluster Ansible Playbook

This Ansible playbook automates the deployment and configuration of a Kafka cluster with Zookeeper ensemble and Kafka UI.

## Components

- Zookeeper Ensemble (3 nodes)
- Kafka Brokers (3+ nodes)
- Kafka UI

## Prerequisites

- Ansible installed on the control machine
- Target Ubuntu servers with SSH access
- Python 3 installed on all servers

## Directory Structure

├── add-broker.yml
├── group_vars
│   ├── all.yml
│   └── kafka_brokers.yml
├── inventory
│   └── hosts.yml
├── kafka
├── kafka.pub
├── roles
│   ├── common
│   ├── kafka
│   ├── kafka-ui
│   └── zookeeper
└── site.yml

## Configuration

1. Update `inventory/hosts.yml` with your server details.
2. Adjust variables in `group_vars/all.yml` and `group_vars/kafka_brokers.yml` as needed.
3. Ensure the `kafka` SSH private key is present in the project root.

## Usage

To deploy the entire Kafka cluster:

```bash
ansible-playbook -i inventory/hosts.yml site.yml
```

## To add a new Kafka broker:

1. Add the new broker details to inventory/hosts.yml under kafka_brokers.
2. Run the add-broker playbook:

```bash
ansible-playbook -i inventory/hosts.yml add-broker.yml
```
## Roles
**common**: Sets up common system packages and Java.
**zookeeper**: Installs and configures Zookeeper ensemble.
**kafka**: Installs and configures Kafka brokers.
**kafka-ui**: Deploys Kafka UI using Docker.

