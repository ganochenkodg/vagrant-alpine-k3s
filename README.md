# vagrant-alpine-k3s

### description
Install alpine+k3s+containerd:

[Vagrant](https://www.vagrantup.com/) - a tool that lets you create and configure lightweight, reproducible, and portable development environments in different hypervisors.

[Virtualbox](https://www.virtualbox.org/) - a free and open-source hosted hypervisor for x86 virtualization, developed by Oracle Corporation.

[K3s](https://k3s.io) - Lightweight Kubernetes

### usage
1. [Install Vagrant](https://www.vagrantup.com/docs/installation/) and [Virtualbox](https://www.virtualbox.org/wiki/VBoxInstallAndRun).
2. Clone this repository and run `cd vagrant-alpine-k3s && vagrant up`. During the launch process, you will be required to enter the root password. After that kubernetes cluster will be raised up using Ansible.

```
/s/v/vagrant-alpine-k3s# vagrant up
All Plugin Dependencies already installed
Bringing machine 'alpine-k3s' up with 'virtualbox' provider...
==> alpine-k3s: Importing base box 'generic/alpine314'...
==> alpine-k3s: Matching MAC address for NAT networking...
==> alpine-k3s: Checking if box 'generic/alpine314' version '3.5.2' is up to date...
==> alpine-k3s: Setting the name of the VM: vagrant-alpine-k3s_alpine-k3s_1637510888675_87271
==> alpine-k3s: Clearing any previously set network interfaces...
==> alpine-k3s: Preparing network interfaces based on configuration...
    alpine-k3s: Adapter 1: nat
    alpine-k3s: Adapter 2: hostonly
==> alpine-k3s: Forwarding ports...
    alpine-k3s: 22 (guest) => 2222 (host) (adapter 1)
==> alpine-k3s: Running 'pre-boot' VM customizations...
==> alpine-k3s: Booting VM...
==> alpine-k3s: Waiting for machine to boot. This may take a few minutes...
    alpine-k3s: SSH address: 127.0.0.1:2222
    alpine-k3s: SSH username: vagrant
    alpine-k3s: SSH auth method: private key
    alpine-k3s:
    alpine-k3s: Vagrant insecure key detected. Vagrant will automatically replace
    alpine-k3s: this with a newly generated keypair for better security.
    alpine-k3s:
    alpine-k3s: Inserting generated public key within guest...
    alpine-k3s: Removing insecure key from the guest if it's present...
    alpine-k3s: Key inserted! Disconnecting and reconnecting using new SSH key...
==> alpine-k3s: Machine booted and ready!
==> alpine-k3s: Checking for guest additions in VM...
==> alpine-k3s: Setting hostname...
==> alpine-k3s: Configuring and enabling network interfaces...
==> alpine-k3s: [vagrant-hostmanager:guests] Updating hosts file on active guest virtual machines...
==> alpine-k3s: [vagrant-hostmanager:host] Updating hosts file on your workstation (password may be required)...
==> alpine-k3s: Running provisioner: hostmanager...
==> alpine-k3s: Running provisioner: shell...
    alpine-k3s: Running: inline script
    alpine-k3s: fetch https://sjc.edge.kernel.org/alpine/v3.14/main/x86_64/APKINDEX.tar.gz
    alpine-k3s: fetch https://sjc.edge.kernel.org/alpine/v3.14/community/x86_64/APKINDEX.tar.gz
    alpine-k3s: (1/8) Installing libbz2 (1.0.8-r1)
    alpine-k3s: (2/8) Installing expat (2.4.1-r0)
    alpine-k3s: (3/8) Installing libffi (3.3-r2)
    alpine-k3s: (4/8) Installing gdbm (1.19-r0)
    alpine-k3s: (5/8) Installing libgcc (10.3.1_git20210424-r2)
    alpine-k3s: (6/8) Installing libstdc++ (10.3.1_git20210424-r2)
    alpine-k3s: (7/8) Installing mpdecimal (2.5.1-r1)
    alpine-k3s: (8/8) Installing python3 (3.9.5-r1)
    alpine-k3s: Executing busybox-1.33.1-r3.trigger
    alpine-k3s: OK: 213 MiB in 96 packages
==> alpine-k3s: Running provisioner: ansible...
    alpine-k3s: Running ansible-playbook...

PLAY [all] *********************************************************************

TASK [Gathering Facts] *********************************************************
[WARNING]: Platform linux on host alpine-k3s is using the discovered Python
interpreter at /usr/bin/python3, but future installation of another Python
interpreter could change this. See https://docs.ansible.com/ansible/2.9/referen
ce_appendices/interpreter_discovery.html for more information.
ok: [alpine-k3s]

TASK [install_k3s : Add cgroups to /etc/fstab] *********************************
changed: [alpine-k3s]

TASK [install_k3s : Define cgroup mount points] ********************************
changed: [alpine-k3s]

TASK [install_k3s : Install k3s] ***********************************************
[WARNING]: Consider using the get_url or uri module rather than running 'curl'.
If you need to use command because get_url or uri is insufficient you can add
'warn: false' to this command task or set 'command_warnings=False' in
ansible.cfg to get rid of this message.
changed: [alpine-k3s]

TASK [install_k3s : Wait for nodes to be ready] ********************************
FAILED - RETRYING: Wait for nodes to be ready (20 retries left).

FAILED - RETRYING: Wait for nodes to be ready (19 retries left).
FAILED - RETRYING: Wait for nodes to be ready (18 retries left).
FAILED - RETRYING: Wait for nodes to be ready (17 retries left).
changed: [alpine-k3s]

TASK [install_k3s : Install nginx Ingress] *************************************
changed: [alpine-k3s]

TASK [install_helm : Install Helm] *********************************************
changed: [alpine-k3s]

TASK [install_helm : Create directory .kube] ***********************************
changed: [alpine-k3s]

TASK [install_helm : Copy config file to user home directory] ******************
changed: [alpine-k3s]

TASK [install_helm : Copy helm chart] ******************************************
changed: [alpine-k3s]

PLAY RECAP *********************************************************************
alpine-k3s                 : ok=10   changed=9    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
```
