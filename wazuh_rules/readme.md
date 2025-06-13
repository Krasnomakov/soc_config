# Wazuh Custom Rules

This directory contains custom Wazuh rules for security monitoring and alerting. These rules are designed to enhance the detection capabilities of your Wazuh deployment.

## Contents

- `local-rules.xml`: Custom Wazuh rules for specific security monitoring scenarios
  - Includes rules for detecting OS Credentials Dump Attack (MITRE ATT&CK T1003.001)
  - Additional custom rules for enhanced security monitoring

## Installation Instructions

1. Access the Wazuh Dashboard
   - Open your web browser and navigate to the Wazuh Dashboard
   - Log in using your default credentials

2. Navigate to Rules Management
   - Go to Server Management
   - Select Rules
   - Search for "local_rules"

3. Update Rules
   - Open `local_rules.xml`
   - Copy the contents from the `local-rules.xml` file in this repository
   - Overwrite the existing content
   - Save the changes

## Testing the Rules

1. Ensure your Wazuh agent is properly installed on the target Windows machine
2. Verify the agent is connected to the Wazuh manager
3. Test the rules by:
   - Monitoring the Wazuh dashboard for alerts
   - Checking the agent's logs for rule triggers
   - Verifying that the OS Credentials Dump Attack detection is working

## MITRE ATT&CK Coverage

The rules in this directory cover the following MITRE ATT&CK technique:
- T1003.001 - OS Credential Dumping: LSASS Memory
  - For more information, visit: https://attack.mitre.org/techniques/T1003/001/

## Maintenance

- Regularly review and update rules as needed
- Monitor for false positives and adjust rules accordingly
- Keep track of new security threats and update rules to address them

## Troubleshooting

If rules are not working as expected:
1. Verify the rules are properly loaded in the Wazuh manager
2. Check the agent's connection status
3. Review the Wazuh manager logs for any errors
4. Ensure the agent has the necessary permissions to monitor the required events 
