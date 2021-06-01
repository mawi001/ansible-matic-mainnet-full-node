# Deploy matic-mainnet-full-node

Push button deployment of Matic/Polygon mainnet full node

Polygon is a protocol and a framework for building and connecting Ethereum-compatible blockchain networks. Aggregating scalable solutions on Ethereum supporting a multi-chain Ethereum ecosystem.

This repo contains an Ansible playbook to deploy the heimdall and bor components.

# Requirements

System specs for the full node

Minimum system requirements are as follows:

16 GiB of memory
4 core CPU (t2 xLarge)
Minimum 150GB disk (make sure it is extendable)

OS

- account with sudo access to perform tasks as root
- internet access

# What is managed

All tasks required to run heimdall and bor in a docker-compose setup are managed.

- manage workspace
- prepare the node for docker deployments
- manage docker-compose config
- build docker images
- download snapshots for heimdall and bor to get in sync faster then from scratch
- extract snapshots to heimdall and bor data dir
- manage heimdall and bor docker compose services

# Usage with vagrant (development)

To deploy a development environment

Manage Ubuntu 18.04 VM with vagrant and provision Polygon Mainnet full node with Ansible

```sh
vagrant up
```

On first boot this will provision the instance.

If you want to provision again and run the playbook run:

```sh
vagrant provision
```

# Usage on a clean install

Tested with Ubuntu 18.04

Clone this repo
```
git clone https://github.com/mawi001/ansible-matic-mainnet-full-node.git
```

Install Ansible
```sh
./run.sh
```

Run Ansible playbook to deploy to localhost

```sh
cd ansible
ansible-playbook -v -i hosts deploy.yml
```
