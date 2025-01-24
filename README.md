# community.sap_operations Ansible Collection

This Ansible Collection executes various SAP Systems operational tasks, which can be used day-to-day individually or combined for more complex regular maintenance automation

## Functionality

This Ansible Collection executes various SAP Systems operational tasks, including:

- **OS configuration Post-install of SAP Software**
  - Create ansible user for managing systems
  - Update /etc/hosts file
  - Update SSH authorized known hosts file
  - Update firewall port entries based on SAP System instance numbers
- **SAP administration tasks**
  - Start/Stop of SAP HANA and SAP NetWeaver (in any configuration)
  - Update SAP profile files
  - Execute SAP RFCs

## Contents

An Ansible Playbook can call either an Ansible Role, or the individual Ansible Modules:
- **Ansible Roles** (runs multiple Ansible Modules)
- **Ansible Modules** (and adjoining Python/Bash Functions)

For further information regarding the development, code structure and execution workflow please read the [Development documentation](./docs/DEVELOPMENT.md).

Within this Ansible Collection, there are various Ansible Roles and Ansible Modules.

#### Ansible Roles

| Name &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; | Summary |
| :-- | :-- |
| [os_ansible_user](/roles/os_ansible_user) | creates Ansible user `ansadm` with ssh key |
| [os_etchosts](/roles/os_etchosts) | updates `/etc/hosts` |
| [os_knownhosts](/roles/os_knownhosts) | updates known hosts file `/.ssh/known_hosts` |
| [sap_control](/roles/sap_control) | starting and stopping SAP systems |
| [sap_firewall](/roles/sap_firewall) | update service `firewalld` for generic / sap nw / sap hana related ports |
| [sap_profile_update](/roles/sap_profile_update) | update default and instance profiles |
| [sap_rfc](/roles/sap_rfc) | executes SAP RFCs |

#### Ansible Modules

| Name &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; | Summary |
| :-- | :-- |
| [sap_operations.sap_facts](/docs/module_sap_facts.md) | gather SAP facts in a host (e.g. SAP System IDs and SAP System Instance Numbers of either SAP HANA database server or SAP NetWeaver application server) |
| [sap_operations.sap_monitor_hana_status](/docs/module_sap_monitor.md) | check status of running SAP HANA database server |
| [sap_operations.sap_monitor_nw_status](/docs/module_sap_monitor.md) | check status of running SAP NetWeaver application server |
| [sap_operations.sap_monitor_nw_perf](/docs/module_sap_monitor.md) | check host performance metrics from SAP NetWeaver Primary Application Server (PAS) instance |
| [sap_operations.sap_monitor_nw_response](/docs/module_sap_monitor.md) | check system response time metrics from SAP NetWeaver Primary Application Server (PAS) instance |

## Execution examples

There are various methods to execute the Ansible Collection, dependant on the use case. For more information, see [Execution examples with code samples](./docs/EXEC_EXAMPLES.md) and the summary below:

| Execution Scenario | Use Case | Target |
| --- | --- | --- |
| Ansible Playbook <br/>-> source Ansible Collection <br/>-> execute Ansible Task <br/>--> run Ansible Module <br/>---> run Python/Bash Functions | Simple executions with a few activities | Localhost or Remote |
| Ansible Playbook <br/>-> source Ansible Collection <br/>-> execute Ansible Task <br/>--> run Ansible Role <br/>---> run Ansible Module <br/>----> run Python/Bash Functions <br/>--> run Ansible Role<br/>---> ... | Complex executions with various interlinked activities;<br/> run in parallel or sequentially | Localhost or Remote |
| Python/Bash Functions | Simple testing or non-Ansible use cases | Localhost |

## Requirements

### Control Nodes
Operating system:
- SUSE Linux Enterprise Server for SAP applications 15 SP5+
- SUSE Linux Enterprise Server for SAP applications 16

Python: 3.11 or higher

Ansible:
  - 9.9.x for SLES 15
  - 10 or higher for SLES 16

Ansible-core:
  - 2.16.x for SLES 15
  - 2.17 or higher for SLES 16

### Managed Nodes
Operating system:
- SUSE Linux Enterprise Server for SAP applications 15 SP5+
- SUSE Linux Enterprise Server for SAP applications 16

Python:
  - 3.6 or higher when using ansible-core 2.16.x
  - 3.11 or higher when using ansible-core 2.17 or higher.

## Testing
This Ansible Collection was tested across different Operating Systems, SAP products and scenarios. You can find examples of some of them below.

Operating systems:
- SUSE Linux Enterprise Server for SAP applications 15 SP5+
- SUSE Linux Enterprise Server for SAP applications 16

## License

- [Apache 2.0](./LICENSE)

## Contributors

Contributors to the Ansible Roles within this Ansible Collection, are shown within [/docs/contributors](./docs/CONTRIBUTORS.md).
