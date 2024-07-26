https://github.com/olafhartong/Invoke-Phant0m

- ScriptBlockText: Dbghelp::SymLoadModuleEx
- ScriptBlockText: MappedFile
- ScriptBlockText: OpenThread
- ScriptBlockText: TerminateThread
- ScriptBlockText: SuspendThread


```kusto
DeviceEvents
| where Timestamp > ago(30d)
| where ActionType == "PowerShellCommand"
| extend Command = tostring(parse_json(AdditionalFields)["Command"])
| distinct Command
| where Command contains "Dbghelp::SymLoadModuleEx" or
        Command contains "MappedFile" or
        Command contains "OpenThread" or
        Command contains "TerminateThread" or
        Command contains "SuspendThread"
```