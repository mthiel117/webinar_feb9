# Network Automation

![Network Automation](https://img.shields.io/badge/Network%20Automation-blue&?style=for-the-badge&logo=ansible)

## Summary

Building your own automation workflow with open source tools: Ansible, NetBox and Git.

To get started, setup your machine with the suggested tools below.  The roadmap gives you a path to follow and an example Ansible Playbook is shown below.  Give it a try!

## Install these as part of your Automation Toolbox

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

## Example Python Script - Gather Info from Network Devices

Clone the webinar repo from Github

```text
git clone https://github.com/mthiel117/webinar_feb9.git
```

If running python2 install this jsonrpclib module

```text
pip install jsonrpclib
```

If running python3 install this jsonrpclib-pelix module

```text
pip install jsonrpclib-pelix
```

Change directory and run script

```text
cd python-example
./net-info.py
```

## Example Playbook - Create Base Configs from CSV File

The following playbook creates a unique base device configuration for each row in the CSV file.

| File/Directory | Description |
| -------- | -------- |
| **./playbooks/create_base_configs.yml** | Playbook |
| **./templates/base-cfg.j2** | Jinja Template |
| **./datafiles/devices.csv** | CSV File of Device with header row (used for variable names in Jinja) |
| **./base-configs/** | Directory for rendered configuration files |

Test it out: (*requires ansible to be installed*)

```text
git clone https://github.com/mthiel117/webinar_feb9.git
cd csv-playbook-example
ansible-playbook create_base_configs.yml
```

Look for config files inside the **./base-configs/** directory.
