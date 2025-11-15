### SSH Key Management

To manage SSH access, create the following files in this directory:

*   **`allowed.pub`**: Place your authorized public SSH keys here (one per line). These keys will be granted access.
*   **`blocked.pub`**: Place public SSH keys here that you wish to explicitly revoke or block access for (e.g., from a compromised device or an old account).