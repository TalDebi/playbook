# Ansible Playbook Setup Guide

## 📌 Overview
This playbook performs the following tasks on the specified VMs:
1. Creates a text file (`ansible-text-file`) in `/tmp/` with your name.
2. Reads and prints the file's contents.
3. Installs the `python-devel` package.
4. Deletes the text file.

## 📂 Folder Structure
```
playbook/
├── inventory.ini   # Hosts and connection details
├── playbook.yml    # Ansible playbook
├── group_vars/
│   └── dana_vms.yml # Group variables
├── ansible.cfg     # Configuration file
└── README.md       # This guide
```

## 🔑 Setting Up Passwordless SSH Access
Before running Ansible, ensure passwordless SSH authentication is set up:

1. **Generate SSH Key** (on `dana-dev-x` VM):
   ```bash
   ssh-keygen -t rsa -b 4096
   ```
   Press **Enter** to accept the default path.

2. **Copy Key to Target VMs**:
   ```bash
   ssh-copy-id your_user@192.168.1.101
   ssh-copy-id your_user@192.168.1.102
   ssh-copy-id your_user@192.168.1.103
   ```

3. **Test SSH Connection**:
   ```bash
   ssh your_user@192.168.1.101
   ```
   If logged in without a password prompt, it's working!

## 🛠 Running the Playbook
1. **Ensure Ansible is installed** (on `dana-dev-x`):
   ```bash
   sudo dnf install ansible
   ```

2. **Navigate to the playbook folder**:
   ```bash
   cd playbook
   ```

3. **Run the playbook**:
   ```bash
   ansible-playbook playbook.yml
   ```

4. **Verify Execution**:
   ```bash
   ansible dana_vms -m ping
   ```

## ✅ Expected Output
You should see the file contents printed, `python-devel` installed, and the file deleted.

---
**Now your setup is fully automated! 🚀**
