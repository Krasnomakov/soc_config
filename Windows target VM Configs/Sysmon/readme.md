# Microsoft Sysmon Configuration

This directory contains configuration files for Microsoft Sysmon (System Monitor), a Windows system service and device driver that monitors and logs system activity to the Windows event log.

## Contents

- `Sysmon64.exe`: The Sysmon executable
- `sysmonconfig-export.xml`: Configuration file for Sysmon monitoring rules

## Installation Instructions

1. Download Sysmon
   - Download Sysmon from the official Microsoft website
   - Place the executable in this directory

2. Install Sysmon with Configuration
   ```powershell
   .\Sysmon64.exe -i sysmonconfig-export.xml -accepteula
   ```

## Configuration Details

The provided configuration file (`sysmonconfig-export.xml`) includes monitoring for:
- Process creation and termination
- Network connections
- File creation and modification
- Registry changes
- WMI events
- Driver loading
- Image loading
- CreateRemoteThread events

## Verification

After installation, verify Sysmon is running:
1. Open Event Viewer
2. Navigate to Applications and Services Logs > Microsoft > Windows > Sysmon > Operational
3. Check for Sysmon event logs

## Event Categories

Sysmon logs the following types of events:
- Event ID 1: Process creation
- Event ID 2: A process changed a file creation time
- Event ID 3: Network connection
- Event ID 4: Sysmon service state changed
- Event ID 5: Process terminated
- Event ID 6: Driver loaded
- Event ID 7: Image loaded
- Event ID 8: CreateRemoteThread
- Event ID 9: RawAccessRead
- Event ID 10: ProcessAccess
- Event ID 11: FileCreate
- Event ID 12: RegistryEvent (Create/Delete)
- Event ID 13: RegistryEvent (Value Set)
- Event ID 14: RegistryEvent (Key and Value Rename)
- Event ID 15: FileCreateStreamHash
- Event ID 16: Sysmon configuration changed
- Event ID 17: Pipe Created
- Event ID 18: Pipe Connected
- Event ID 19: WmiFilter
- Event ID 20: WmiConsumer
- Event ID 21: WmiConsumerFilter
- Event ID 22: DNSEvent
- Event ID 23: FileDelete
- Event ID 24: ClipboardChange
- Event ID 25: ProcessTampering
- Event ID 26: FileDeleteDetected
- Event ID 27: FileBlockExecutable
- Event ID 28: FileBlockShredding
- Event ID 29: FileExecutableDetected

## Maintenance

- Regularly review Sysmon logs for suspicious activity
- Update the configuration file as needed for new monitoring requirements
- Monitor Sysmon service status
- Keep Sysmon updated to the latest version

## Troubleshooting

If Sysmon is not working as expected:
1. Verify the Sysmon service is running
2. Check Event Viewer for any Sysmon-related errors
3. Ensure the configuration file is properly formatted
4. Verify you have administrative privileges
5. Check Windows Event Log service is running

## Security Considerations

- Sysmon requires administrative privileges to install
- The configuration file should be protected from unauthorized modifications
- Regular review of Sysmon logs is essential for security monitoring
- Consider implementing log forwarding to a central logging solution