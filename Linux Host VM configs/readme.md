These are the files for VM hosting SOC components:
- Wazuh 
- Caldera 
- Snort 

----

Install wazuh in docker 
Must install Docker for VM in advance 

Guide
https://documentation.wazuh.com/current/deployment-options/docker/docker-installation.html 

Place ossec.conf in this location:
sudo cat /var/lib/docker/volumes/single-node_wazuh_etc/_data/ossec.conf

Or ensure you have 

<jsonout_output>yes</jsonout_output>
<alerts_log>yes</alerts_log>
<logall>yes</logall>
<logall_json>yes</logall_json>

in your ossec.conf in same or simialr location. 

It ensures wazuh logs all events 

----

Optionally add more rules
Wazuh-Rules by SOC Fortress (Open-Source SOC)
https://github.com/socfortress/Wazuh-Rules


Summary of steps neccessary to add SOC Fortress Wazuh rules if you use Docekr installation

Download rules for github repo 
https://github.com/socfortress/Wazuh-Rules 

1. Step 1: Work as root
   Purpose: Ensure full control of Docker volume
   Key Commands: sudo su
   Result: Full root access under /var/lib/docker/volumes/...

2. Step 2: Fix ownership
   Purpose: Assign Wazuh user ownership (UID/GID 1000) of mounted etc data
   Key Commands: cd /var/lib/docker/volumes/single-node\_wazuh\_etc/\_data and chown -R 1000:1000 .
   Result: Container process can read and modify the files

3. Step 3: Tighten directory permissions
   Purpose: Allow owner and group traverse/read, block others
   Key Commands: find . -type d -exec chmod 750 {} ;
   Result: Wazuh can descend tree; outsiders blocked

4. Step 4: Tighten file permissions
   Purpose: Read/write for owner, read for group, none for others
   Key Commands: find . -type f -exec chmod 640 {} ;
   Result: Rules readable by Wazuh, not world-readable

5. Step 5 (Optional): SELinux/AppArmor label adjustment
   Purpose: Align labels if host security blocks the volume
   Key Commands: chcon -R --reference=/var/ossec/etc .
   Result: Matches host policy so container can open files

6. Step 6: Declare extra rules directory in ossec.conf
   Purpose: Instruct Wazuh to load external rules path
   Key Commands: Add the \<rule\_dir>/var/ossec/etc/rules\</rule\_dir> entry in the ruleset section of ossec.conf
   Result: Manager parses and loads the directory on restart

7. Step 7: Reload or restart Wazuh
   Purpose: Apply new permissions and configuration changes
   Key Commands: systemctl restart wazuh-manager or docker compose restart wazuh.manager
   Result: New rules active; no permission errors

Why the ossec.conf edit mattered
Even with correct filesystem permissions, Wazuh ignores any directory not explicitly listed under a rule\_dir stanza. Setting UNIX permissions removed the OS-level block. Adding the path in ossec.conf removed the application-level block, ensuring all rules are loaded and accessible without permission denied errors.


----

Use docker commands to access and check wazuh logs and alerts 
Find necessary files 

---

Use firewall_rules to adjust your ufw firewall rules