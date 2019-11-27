# ansible

## Ansible

## Inventory

Inventory is a set of hosts, optionally sorted into groups A simple inventory can be a set of ips or hosts We can also categorize hosts into different groups

Hosts can be matched using patterns

## Taks

Expressed in Yaml

## Moduels

The code the taks uses to perform work

## Playbooks

YAML files conanin on or more plays

Play are one or more tasks

## Generate ssh key and use public-key authentication to connect to remote host

```bash
ssh-keygen
ssh-copy-id -i mykey user@host
```

Make sure on the remote host, `/etc/ssh/sshd_config` contains **PubkeyAuthentication yes**

At this moment on the management machine, you can use ssh-agent and add key to agent

```bash
ssh-agent
add-key mykey
```

## Build hosts

Ansible hosts support INI and YAML

```text
[group1]
host1
host2 ansible_port=22 ansible_host=10.0.0.2
10.0.0.3
host4 ansible_host=10.0.0.4 ansible_ssh_private_key_file=/home/xhuang/.ssh/mykey

[all:vars]
ansible_connection=local
```

The last line is necessary when you run ansible playbook on localhost

