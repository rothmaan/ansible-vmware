This Ansible playbook automates the migration of a VM from VMware vCenter to OpenShift Virtualization. It performs the following tasks:

1. Gathers information about the specified VMware VM.
2. Creates a migration plan in OpenShift using the k8s module
3. Executes the migration plan using the k8s module
4. Monitors the migration progress until completion using the k8s_info module.

# Prerequisites
Required Ansible Modules:

ansible-galaxy collection install community.vmware
ansible-galaxy collection install community.general
pip install openshift pyvmomi

tree vm_migration
vm_migration
├── README.md           # Documentation file providing an overview and instructions for the role
├── defaults
│   └── main.yml        # Default variables for the role with placeholders for vCenter details and VM name
├── tasks
│   └── main.yml        # Main tasks file containing the sequence of actions to gather VM info, create and execute migration plan, and monitor progress
└── vars
    └── main.yml        # Specific variables for the role, including vCenter details and the name of the VM to migrate


ansible-playbook -i localhost, playbook.yml -e @vars.yml

