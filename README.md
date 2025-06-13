# SOC Configuration Repository

This repository contains configuration files and rules for setting up and maintaining a Security Operations Center (SOC) environment. It includes configurations for both Linux and Windows systems, as well as Wazuh security monitoring rules.

## Repository Structure

### `wazuh_rules/`
Contains custom Wazuh rules for security monitoring and alerting. This directory includes:
- `local-rules.xml`: Custom Wazuh rules for specific security monitoring scenarios
- `readme.md`: Documentation for the Wazuh rules

### `Linux Host VM configs/`
Configuration files for the Linux host virtual machine, including:
- `firewall_rules`: Network security configurations
- `ossec.conf`: Wazuh agent configuration
- `wazuh_commands_in_docker`: Docker-specific Wazuh commands
- `readme.md`: Detailed documentation for Linux host setup

### `Windows target VM Configs/`
Configuration files for Windows target virtual machines, including:
- `Sysmon/`: Microsoft Sysmon configuration for advanced Windows event monitoring
- `ossec-agent (Wazuh Agent)/`: Wazuh agent configuration for Windows systems

## Getting Started

Each directory contains its own README file with specific instructions for setup and configuration. Please refer to the individual README files in each directory for detailed information about:
- Installation procedures
- Configuration steps
- Usage guidelines
- Troubleshooting tips

## Contributing

When contributing to this repository, please ensure that:
1. All configuration changes are documented
2. README files are updated accordingly
3. Changes are tested in a development environment before deployment

## Security

This repository contains sensitive configuration files. Please ensure that:
- Access is restricted to authorized personnel
- No sensitive credentials are stored in the repository
- All security configurations are regularly reviewed and updated 