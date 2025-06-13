# Windows Target VM Configurations

This directory contains configuration files for setting up Windows target virtual machines with security monitoring capabilities.

## Directory Structure

### `Sysmon/`
Contains Microsoft Sysmon configuration files for advanced Windows event monitoring. Sysmon provides detailed information about process creations, network connections, and other system activities.

### `ossec-agent (Wazuh Agent)/`
Contains configuration files for the Wazuh agent on Windows systems. The Wazuh agent is responsible for:
- System monitoring
- Log collection
- Security event forwarding
- File integrity monitoring

## Setup Instructions

### Sysmon Installation and Configuration
1. Download Sysmon from Microsoft's official website
2. Install Sysmon using the provided configuration
3. Verify the installation by checking Event Viewer > Applications and Services Logs > Microsoft > Windows > Sysmon > Operational

### Wazuh Agent Installation
1. Download the Wazuh agent installer for Windows
2. Run the installer with administrator privileges
3. Configure the agent to connect to your Wazuh manager
4. Verify the connection in the Wazuh dashboard

## Monitoring and Maintenance

### Sysmon
- Regularly review Sysmon logs in Event Viewer
- Update Sysmon configuration as needed for new monitoring requirements
- Monitor for any Sysmon service issues

### Wazuh Agent
- Check agent status in Wazuh dashboard
- Monitor agent logs for any connection issues
- Keep the agent updated to the latest version
- Verify file integrity monitoring is working correctly

## Troubleshooting

### Common Issues
1. Agent Connection Problems
   - Verify network connectivity
   - Check firewall rules
   - Validate agent registration

2. Sysmon Issues
   - Verify Sysmon service is running
   - Check Event Viewer for error messages
   - Validate configuration file syntax

## Security Considerations

- Keep all monitoring tools updated
- Regularly review and update configurations
- Monitor for any unauthorized changes to monitoring configurations
- Ensure proper access controls are in place 