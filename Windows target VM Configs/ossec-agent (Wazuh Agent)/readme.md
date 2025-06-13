# Wazuh Agent Configuration for Windows

This directory contains the configuration file for the Wazuh agent on Windows systems. The configuration is specifically designed to monitor and forward Sysmon events to the Wazuh manager.

## Contents

- `ossec.conf`: Configuration file for the Wazuh agent
  - Configured to collect and forward Sysmon events
  - Includes necessary settings for Windows event log monitoring

## Installation Location

The `ossec.conf` file should be placed in the Wazuh agent installation directory:
```
C:\Program Files (x86)\ossec\ossec.conf
```

## Configuration Details

The provided configuration:
- Enables Windows event log monitoring
- Configures Sysmon event collection
- Sets up secure communication with the Wazuh manager
- Configures log forwarding settings

## Setup Instructions

1. Install Wazuh Agent
   - Download the Windows agent installer from Wazuh
   - Run the installer with administrator privileges
   - Follow the installation wizard

2. Configure the Agent
   - Stop the Wazuh agent service
   - Replace the existing `ossec.conf` with the provided configuration
   - Update the manager IP address in the configuration if needed
   - Start the Wazuh agent service

3. Verify Configuration
   - Check the agent status in the Wazuh dashboard
   - Verify Sysmon events are being received
   - Monitor the agent logs for any errors

## Log Locations

- Agent logs: `C:\Program Files (x86)\ossec\logs\ossec.log`
- Agent alerts: `C:\Program Files (x86)\ossec\logs\alerts\alerts.log`

## Maintenance

- Regularly check agent status in the Wazuh dashboard
- Monitor agent logs for any issues
- Keep the agent updated to the latest version
- Review and update configuration as needed

## Troubleshooting

If the agent is not working as expected:
1. Verify the agent service is running
2. Check the agent logs for errors
3. Ensure the manager IP is correctly configured
4. Verify network connectivity to the manager
5. Check Windows Event Log service is running
6. Verify Sysmon is properly installed and running

## Security Considerations

- The agent requires administrative privileges for installation
- Secure communication between agent and manager is essential
- Regular review of agent logs is recommended
- Keep the agent updated with security patches
- Monitor for any unauthorized configuration changes