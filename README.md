# SDRPi - SDR Station Ansible Setup

This project provides an Ansible playbook for setting up and configuring an SDR (Software Defined Radio) station on a Raspberry Pi running Debian-based 64-bit OS (ARM architecture).

## Features

- Automated system updates and package upgrades
- Unattended updates configuration
- SSH key management with allow/block lists
- NTP synchronization using Chrony
- User creation and management
- Secure SSH configuration (password authentication disabled)
- RTL-SDR driver installation from source
- SDR++ (SDRPlusPlus) installation and setup
- SDR++ server systemd service configuration

## Prerequisites

- Ansible installed on your control machine
- SSH access to the target host
- Target host: Raspberry Pi running Debian-based 64-bit OS (ARM64)

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
ansible-playbook --ask-become-pass -i inventory.ini playbook.yaml
```

This will execute the complete SDR station setup including:
- System updates and basic configuration
- RTL-SDR driver installation
- SDR++ installation and server setup
- Systemd service configuration for SDR++ server

## RTL-SDR Hardware Setup

The playbook automatically installs RTL-SDR drivers from source. For RTL-SDR V4 dongles or manual installation, refer to the official guide: [RTL-SDR V4 Driver Installation](https://www.rtl-sdr.com/V4/)

## SDR++ Server

After running the playbook, SDR++ will be running as a systemd service on the target host. The server listens on port 5259 by default.

### Connecting to SDR++ Server

1. Install SDR++ on your local machine from [https://github.com/AlexandreRouma/SDRPlusPlus](https://github.com/AlexandreRouma/SDRPlusPlus)

2. Launch SDR++ locally

3. In SDR++:
   - Go to the "Source" menu
   - Select "SDR++ Server"
   - Enter the IP address of your SDR station and port 5259
   - Connect to the server
   - Once connected, select your SDR device from the available sources

The SDR++ server allows you to control the SDR hardware remotely while running the processing on your local machine.

## Project Structure

- `playbook.yaml` - Main Ansible playbook with SDR++ setup
- `basic-setup.yaml` - Basic system setup tasks (SSH, NTP, unattended updates)
- `rtl-sdr-install.yaml` - RTL-SDR driver installation tasks
- `inventory.ini` - Ansible inventory file
- `keys/` - SSH key management directory
- `utils/` - Utility playbooks and tasks
- `.devcontainer/` - Development container configuration

## Development

This project includes a dev container configuration for VS Code. Open in VS Code with the Dev Containers extension for a ready-to-use Ansible development environment.