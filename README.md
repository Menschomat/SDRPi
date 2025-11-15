# SDRPi - SDR Station Ansible Setup

This project provides an Ansible playbook for setting up and configuring an SDR (Software Defined Radio) station on a Linux host.

## Features

- Automated system updates and package upgrades
- SSH key management with allow/block lists
- NTP synchronization using Chrony
- User creation and management
- Secure SSH configuration (password authentication disabled)

## Prerequisites

- Ansible installed on your control machine
- SSH access to the target host
- Target host running Ubuntu/Debian-based Linux

## Setup

1. Clone this repository:
   ```bash
   git clone <repository-url>
   cd sdr-station
   ```

2. Configure your inventory in `inventory.ini`:
   ```
   [sdr-station]
   your-host-ip ansible_user=your-user ansible_become=yes
   ```

3. Set up SSH keys in the `keys/` directory:
   - Add authorized public keys to `keys/allowed.pub` (one per line)
   - Add keys to block to `keys/blocked.pub` (one per line)

## Usage

Run the main playbook:
```bash
ansible-playbook -i inventory.ini playbook.yaml
```

This will execute the basic setup and system configuration tasks.

## Project Structure

- `playbook.yaml` - Main Ansible playbook
- `basic-setup.yaml` - Basic system setup tasks
- `inventory.ini` - Ansible inventory file
- `keys/` - SSH key management directory
- `utils/` - Utility playbooks and tasks
- `.devcontainer/` - Development container configuration

## Development

This project includes a dev container configuration for VS Code. Open in VS Code with the Dev Containers extension for a ready-to-use Ansible development environment.