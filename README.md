# kubeadm-vagrant
kubeadm K8s setup on Vagrant cluster


## Runbook

1. [Install Ansible](#install-ansible)
2. [Generate SSH file to Vagrant](#generate-sshfile-to-vagrant)
3. [Run playbook](#run-playbook)

### Install ansible
```
pip install ansible
```
### Generate SSH file to Vagrant

```
vagrant ssh-config > .vagrant-ssh
```
### Run playbook
```
ansible-playbook plays/deploy-play.yaml
```

## Troubleshooting
### Issue with MacOS BigSur

`vagrant up` command can cause the following error:

```
==> kubemaster: Clearing any previously set network interfaces...
There was an error while executing `VBoxManage`, a CLI used by Vagrant
for controlling VirtualBox. The command and stderr is shown below.

Command: ["hostonlyif", "create"]

Stderr: 0%...
Progress state: NS_ERROR_FAILURE
VBoxManage: error: Failed to create the host-only adapter
VBoxManage: error: VBoxNetAdpCtl: Error while adding new interface: failed to open /dev/vboxnetctl: No such file or directory
VBoxManage: error: Details: code NS_ERROR_FAILURE (0x80004005), component HostNetworkInterfaceWrap, interface IHostNetworkInterface
VBoxManage: error: Context: "RTEXITCODE handleCreate(HandlerArg *)" at line 95 of file VBoxManageHostonly.cpp
```

#### Solution:

1. Go into System Preferences->Security & Privacy
2. Unlock the security center
3. Approve the software by Oracle
4. Run `sudo /Library/Application\ Support/VirtualBox/LaunchDaemons/VirtualBoxStartup.sh restart`
