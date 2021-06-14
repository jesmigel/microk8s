# microk8s
MicroK8s ansible deployment to an ESXI Host

### Dependencies
| Dependency | Comments |
| - | - |
| [Ansible](https://docs.ansible.com/) | Configuration management automation tool|
| [ESXI (6.7u3)](https://my.vmware.com/en/group/vmware/evalcenter?p=free-esxi6) | Hypervisor |
| [Python](https://www.python.org/downloads/) | Programming language required to run ansible |
| [Vagrant](https://www.vagrantup.com/docs) | VM manager. Local dev/test environment |
| [Virtualenv](https://docs.python.org/3/tutorial/venv.html) | Python environment isolation |
|||

### Preflight Steps
1. Copy the [sample.env.yaml](./sample.env.yaml) to `env.yaml` and populate the following fields
    - host: # ESXI host
    - user: # esxi user id
    - password: # esxi password

2. Add or remove the [microk8s addons](./ansible/roles/microk8s/defaults/main.yaml). For reference, refer to the [official site](https://microk8s.io/docs/addons)

### Deployment
1. Execute `make up` to deploy a VM, install microk8s and enable the microk8s addons.
2. Execute `make get_kubeconfig` to generate a script that source the kubeconfig.
    - This is a prerequisite to access the dashboard through `kubectle proxy`

### ToDo
- Multi node microk8s to emulate a HA environment