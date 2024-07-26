# List of Stuff we could hunt for

## Windows Firewall Changes
- [ ] Look for changes to the Windows Firewall rules
- [ ] Look for changes to the Windows Firewall settings
- [ ] Look for changes to the Windows Firewall service

``netsh advfirewall show currentprofile state``

## MDNS Stuff

No idea how to get multicast dns info

## Changes to Defender for Endpoint
- [ ] Look for changes to the Defender for Endpoint settings
- [ ] Look for changes to the Defender for Endpoint service
- [ ] Look for changes to the Defender for Endpoint exclusions

``Get-MpPreference``

## Python Script execution

## Office Executes stuff

## WMI

Check for Powershell Codeblocks via WMI
``| where InitiatingProcessFileName == "wmiprvse.exe" or InitiatingProcessParentFileName == "wmiprvse.exe"``

Or use ASR?
``| where ActionType == "AsrPsexecWmiChildProcessAudited"``

check:
- https://github.com/Azure/Azure-Sentinel
- https://unit42.paloaltonetworks.com/attackers-exploit-public-cobalt-strike-profiles/
- https://www.logpoint.com/de/blog/so-erkennen-sie-verdeckte-cobalt-strike-aktivitaeten-in-ihrem-unternehmen/