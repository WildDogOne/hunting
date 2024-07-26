# FalconForce Queries

## License

All rules from the Author FalconForce fall under their [License](https://github.com/FalconForceTeam/FalconFriday/blob/master/LICENSE)

## References Used
- https://github.com/FalconForceTeam/FalconFriday/

## Falcon Rules Implemented
### Command and Control
| Falcon Rule      | Status       | Implemented Rule                              |
| ---------------- | ------------ | --------------------------------------------- |
| T1071.001.md     | Incompatible |                                               |
| T1105-WIN-001.md | Implemented  | queries/command and control/certutil CLI.yaml |

### Credential Access
| Falcon Rule        | Status       | Implemented Rule                                                    |
| ------------------ | ------------ | ------------------------------------------------------------------- |
| T1003.001-WIN.md   | Implemented  | queries/credential access/LSASS Dumping using Debug Privileges.yaml |
| T1134.001-WIN.md   | Implemented  | queries/credential access/PRT Credential Stealing.yml               |
| T1528-Azure-001.md | Incompatible |                                                                     |
| T1556.001-WIN.md   | Incompatible |                                                                     |
| T1134.001-WIN.md   | Implemented  | queries/credential access/NTLM Relay Attack.yml                     |
| T1558.002-WIN.md   | Incompatible |                                                                     |

### Defense Evasion
| Falcon Rule                                         | Status       | Implemented Rule                                                          |
| --------------------------------------------------- | ------------ | ------------------------------------------------------------------------- |
| 0xFF-0161-Overly_permissive_security_group-AWS.md   | Incompatible |                                                                           |
| 0xFF-0546-Process_Injection_Initiated_By_MMC-Win.md | Implemented  | queries/defense evasion/Process Injection Initiated By MMC.yml            |
| T1036-Azure-001.md                                  | Incompatible |                                                                           |
| T1036-Azure-002.md                                  | Incompatible |                                                                           |
| T1036-WIN-001.md                                    | Implemented  | queries/defense evasion/Invalid Code Signature - Network Connections.yaml |
| T1036-WIN-002.md                                    | Implemented  | queries/defense evasion/Rename System Utilities.yaml                      |
| T1036-WIN-003.md                                    | Implemented  | queries/defense evasion/Match Legitimate Name or Location.yml             |
| T1036.003-WIN-001.md                                | Implemented  | queries/defense evasion/Rename System Utilities.yaml                      |
| T1036.005-WIN-001.md                                | Implemented  | queries/defense evasion/Match Legitimate Name or Location.yml             |
| T1127-WIN-001.md                                    | Not Feasible |                                                                           |
| T1211-Azure-001.md                                  | Incompatible |                                                                           |
| T1218-WIN-001.md                                    | Implemented  | queries/defense evasion/Suspicious CPL files.yml                          |
| T1562-WIN-001.md                                    | Implemented  | queries/defense evasion/Disable or Modify MDE.yml                         |

### Discovery
| Falcon Rule                                                        | Status       | Implemented Rule                                                    |
| ------------------------------------------------------------------ | ------------ | ------------------------------------------------------------------- |
| 0xFF-0239-Discovery_Commands_Executed_from_Instance_Profile-AWS.md | Incompatible |                                                                     |
| ADWS_Connection_from_Process_Injection_Target-Win.md               | Implemented  | queries/discovery/AWDS Connection from Process Injection Target.yml |
| ADWS_Connection_from_Unexpected_Binary-Win.md                      | Implemented  | queries/discovery/ADWS Connection from Unexpected Binary.yml        |
| AD_Data_Collection_LDAP_Filter_Client_Side.md                      | Implemented  | queries/discovery/Active Directory Data Collection Client Side.yml  |
| AD_Data_Collection_LDAP_Filter_Server_Side_MDI.md                  | Implemented  | queries/discovery/Active Directory Data Collection Server Side.yml  |
| AD_Data_Collection_Number_of_Objects_Accessed.md                   | Incompatible |                                                                     |

### Execution

| Falcon Rule                                                             | Status         | Implemented Rule                                                             |
| ----------------------------------------------------------------------- | -------------- | ---------------------------------------------------------------------------- |
| 0xFF-0544-Script_Interpreter_Loading_DotNet_Assembly_From_Memory-Win.md | Implemented    | queries/execution/Script Interpreter Loading DotNet Assembly From Memory.yml |
| T1059.001-WIN-001.md                                                    | Implemented    | queries/execution/PowerShell - System.Management.Automation.yml              |
| T1204-WIN-001.md                                                        | Implemented    | queries/execution/User-Execution - Started Untrusted Binaries.yaml           |
| T1204-WIN-001.md                                                        | Implemented    | queries/execution/User-Execution - Process Injection.yaml                    |
| T1204-WIN-001.md                                                        | Implemented    | queries/execution/User-Execution - cscript, wscript, mshta as Host.yaml      |
| T1559-WIN-001.md                                                        | Implemented    | queries/execution/Suspicious Named Pipes.yml                                 |
| T1611-WIN-001.md                                                        | Implemented    | queries/execution/SQL Server spawning suspicious child process.yml           |
| T1611-WIN-002.md                                                        | Not Applicable |                                                                              |

### Impact

| Falcon Rule        | Status       | Implemented Rule |
| ------------------ | ------------ | ---------------- |
| T1490-Azure-001.md | Incompatible |                  |

### Initial Access

| Falcon Rule                                   | Status      | Implemented Rule                                        |
| --------------------------------------------- | ----------- | ------------------------------------------------------- |
| 0xFF-0545-Suspicious_MSC_File_Launched-Win.md | Implemented | queries/initial access/Suspicious MSC File Launched.yml |
| falcon.T1110.003-WIN-001                      | Implemented | queries/initial access/EntraID - Password Spraying.yml  |
| falcon.T1110.003-WIN-002                      | Implemented | queries/initial access/EntraID - Password Spraying.yml  |
| T1566-WIN-001.md                              | Implemented | queries/initial access/Office Execution.yml             |
| T1566-WIN-002.md                              | Implemented | queries/initial access/Spearphishing link.yml           |

### Lateral Movement

| Falcon Rule      | Status      | Implemented Rule                                                |
| ---------------- | ----------- | --------------------------------------------------------------- |
| T1021-WIN-001.md | Implemented | queries/lateral movement/SCM Missuse.yml                        |
| T1021-WIN-002.md | Implemented | queries/lateral movement/Distributed Component Object Model.yml |

### Persistence

| Falcon Rule                                                           | Status       | Implemented Rule                                                          |
| --------------------------------------------------------------------- | ------------ | ------------------------------------------------------------------------- |
| 0xFF-0237-Password_Assigned_to_Existing_IAM_User-AWS.md               | Incompatible |                                                                           |
| 0xFF-0238-Assume_Role_Added_from_Unknown_External_Account-AWS.md      | Incompatible |                                                                           |
| 0xFF-0240-Instance_Profile_Credentials_Used_from_Unexpected_IP-AWS.md | Incompatible |                                                                           |
| T1053.005-WIN-001.md                                                  | Implemented  | queries/persistence/Scheduled Task.yml                                    |
| T1098-WIN-001.md                                                      | Incompatible |                                                                           |
| T1098-WIN-002.md                                                      | Incompatible |                                                                           |
| T1176-WIN-001.md                                                      | Implemented  | queries/persistence/Chrome Extensions.yml                                 |
| T1543.003-WIN-001.md                                                  | Implemented  | queries/persistence/Create or Modify System Process - Windows Service.yml |
| T1546.015-WIN-001.md                                                  | Implemented  | queries/persistence/Component Object Model Hijacking - Vault7 trick.yml   |

### Privilege Escalation
| Falcon Rule          | Status      | Implemented Rule                                                                                                   |
| -------------------- | ----------- | ------------------------------------------------------------------------------------------------------------------ |
| T1055-WIN-001.md     | Implemented | queries/privilege escalation/Process Injection with CreateRemoteThread.yml                                         |
| T1055.002-WIN-001.md | Implemented | queries/privilege escalation/Process injection via NtAllocateVirtualMemoryRemote by rare or unsigned processes.yml |
| T1055.002-WIN-002.md | Implemented | queries/privilege escalation/Process injection via QueueUserApcRemoteApiCall by rare or unsigned processes.yml     |
| T1134.002-WIN-001.md | Implemented | queries/privilege escalation/Create Process with Token.yml                                                         |
| T1574-WIN-001.md     | Implemented | queries/privilege escalation/DLL Side-Loading.yml                                                                  |
