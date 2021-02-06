# Network Automation

![Network Automation](https://img.shields.io/badge/Network%20Automation-blue&?style=for-the-badge&logo=ansible)

## Summary

Building your own automation workflow with open source tools: Ansible, NetBox and Git.

## Fill Your Automation Toolbox with these tools

- [Microsoft VSCode Editor](https://code.visualstudio.com/Download)
- [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
- [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)
- [Python 3](https://www.python.org/downloads/)
- [Docker Desktop](https://www.docker.com/products/docker-desktop)

## Getting Started Roadmap

There are a few foundational building blocks that you should consider learning that will be building blocks for everything you do going forward.  They are:

- Linux
- Python
- Git

### Start Simple and Expand

- Reporting

  - Low-Risk no changes to the network.  Just read info.
  - Start with scripts that produce automated reports about the network

- Change Device Configuration

  - Automate a task to change a device’s config state, can be simple like syslog server.
  - Expand on this by iterating changes over multiple devices

- Validation

  - Write scripts/playbooks to validate a device's intended state matches operational state.
  - Example:  Do my current LLDP neighbors per device match my Source of Truth?

## Example Playbook - Create Base Configs from CSV File

The following playbook creates a unique base device configuration for each row in the CSV file.

- ./playbooks/create_base_configs.yml - Playbook
- ./templates/base-cfg.j2 - Jinja Template
- ./datafiles/devices.csv - CSV File of Device with header row (used for variable names in Jinja)
- ./base-configs/ - Directory for rendered configuration files

Test it out: (*requires ansible to be installed*)

```text
cd csv-playbook-example
ansible-playbook playbooks/create_base_configs.yml
```

## Resources
