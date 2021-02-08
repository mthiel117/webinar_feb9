# Network Automation

![Network Automation](https://img.shields.io/badge/Network%20Automation-blue&?style=for-the-badge&logo=ansible)

## Summary

Building your own automation workflow with open source tools: Ansible, NetBox and Git.

To get started, setup your machine with the suggested tools below.  The roadmap gives you a path to follow and an example Ansible Playbook is shown below.  Give it a try!

## Getting Started Roadmap

There are a few foundational building blocks that you should consider learning that will be building blocks for everything you do going forward.  They are:

- Linux
- Python
- Git

## Install these as part of your Automation Toolbox

- [Microsoft VSCode Editor](https://code.visualstudio.com/Download)
- [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
- [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)
- [Python 3](https://www.python.org/downloads/)
- [Docker Desktop](https://www.docker.com/products/docker-desktop)

## Example Python Script - Gather Info from Network Devices

Quick example of using the Arista eAPI to gather information (hostname, uptime, mac-address, lldp neighbors, etc...) from a network of switches.

Clone the Repository from Github to your local machine.

**Requirements:**  Git and Python2 or Python3 installed and Arista switches that are reachable from your workstation.  You will need to modify the IP address list of switches in the script to match your environment.

```text
git clone https://github.com/mthiel117/webinar_feb9.git
```

If you are running python2, install **jsonrpclib** module

```text
pip install jsonrpclib
```

If running you are python3, install **jsonrpclib-pelix** module

```text
pip install jsonrpclib-pelix
```

In this example, we have a lab of 5 Arista switches available to query.

```text
cd python-example
./net-info.py
```

Output should look similar to the following:

![output](docs/net-info.png)

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
