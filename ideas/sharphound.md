https://www.secureworks.com/blog/sniffing-out-sharphound-on-its-hunt-for-domain-admin

| LDAP Query                                                                                                                                                                                                                                                                | Description                                                                                                                                                                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| (\|(samaccounttype=268435456)(samaccounttype=268435457)(samaccounttype=536870912)(samaccounttype=536870913)(primarygroupid=\*))                                                                                                                                           | Discover group memberships for [security groups, non-security groups, alias and non-alias](https://learn.microsoft.com/en-us/openspecs/windows_protocols/ms-samr/e742be45-665d-4576-b872-0bc99d1e1fbe) objects that have a primary group ID |
| (&(sAMAccountType=805306369)(!(UserAccountControl:1.2.840.113556.1.4.803:=2)))                                                                                                                                                                                            | Discover computer accounts that are enabled                                                                                                                                                                                                 |
| (\|(samAccountType=805306368)(samAccountType=805306369)(samAccountType=268435456)(samAccountType=268435457)(samAccountType=536870912)(samAccountType=536870913)(objectClass=domain)(&(objectcategory=groupPolicyContainer)(flags=\*))(objectcategory=organizationalUnit)) | Discover [access control lists](https://learn.microsoft.com/en-us/windows-hardware/drivers/ifs/access-control-list) (ACLs) containing security information for objects enumerated                                                           |
| (\|(samaccounttype=268435456)(samaccounttype=268435457)(samaccounttype=536870912)(samaccounttype=536870913)(samaccounttype=805306368)(samaccounttype=805306369)(objectclass=domain)(objectclass=organizationalUnit)(&(objectcategory=groupPolicyContainer)(flags=\*)))    | Discover various AD groups, user accounts, computer accounts and group policies, and pull various field names useful for analysis                                                                                                           |
| (\|(&(&(objectcategory=groupPolicyContainer)(flags=\*))(name=\*)(gpcfilesyspath=\*))(objectcategory=organizationalUnit)(objectClass=domain))                                                                                                                              | Discover AD containers and linked Group Policy Objects (GPOs)                                                                                                                                                                               |
| (&(samaccounttype=805306368)(serviceprincipalname=\*))                                                                                                                                                                                                                    | Discover all [service principal names](https://learn.microsoft.com/en-us/windows/win32/ad/service-principal-names) (SPN) for service accounts                                                                                               |
| (\|(samAccountType=805306368)(samAccountType=805306369)(objectclass=organizationalUnit))                                                                                                                                                                                  | For objects returned, discover all other child user, computer, and organizational unit (OU) objects                                                                                                                                         |
| (objectclass=container)                                                                                                                                                                                                                                                   | For objects returned, discover all child container objects                                                                                                                                                                                  |
| (\|(samAccountType=805306368)(samAccountType=805306369))                                                                                                                                                                                                                  | Discover all the user and computer objects                                                                                                                                                                                                  |
| (objectclass=trusteddomain)                                                                                                                                                                                                                                               | Discover all [trusted domains](https://learn.microsoft.com/en-us/openspecs/windows_protocols/ms-adts/c9efe39c-f5f9-43e9-9479-941c20d0e590)                                                                                                  |


### LDAP Indicators
flags=*
gpcfilesyspath=*
serviceprincipalname=*
objectclass=organizationalUnit
objectclass=container
objectclass=trusteddomain
primarygroupid=*
UserAccountControl:1.2.840.113556.1.4.803:=2
samaccounttype=268435456
samaccounttype=268435457
samaccounttype=536870912
samaccounttype=536870913
sAMAccountType=805306369
samAccountType=805306368
samAccountType=805306369
samAccountType=268435456
samAccountType=268435457
samAccountType=536870912
samAccountType=536870913
samaccounttype=805306368
samaccounttype=805306369

### Kusto

```
IdentityQueryEvents
| where Timestamp > ago(30d)
| extend search_filter = tostring(parse_json(AdditionalFields["SearchFilter"]))
| where isnotempty(search_filter)
| where search_filter contains "flags=*" or
    search_filter contains "gpcfilesyspath=*" or
    search_filter contains "serviceprincipalname=*" or
    search_filter contains "objectclass=organizationalUnit" or
    search_filter contains "objectclass=container" or
    search_filter contains "objectclass=trusteddomain" or
    search_filter contains "primarygroupid=*" or
    search_filter contains "UserAccountControl:" or
    search_filter contains "268435456" or
    search_filter contains "268435457" or
    search_filter contains "536870912" or
    search_filter contains "536870913" or
    search_filter contains "805306369" or
    search_filter contains "805306368" or
    search_filter contains "805306369" or
    search_filter contains "268435456" or
    search_filter contains "268435457" or
    search_filter contains "536870912" or
    search_filter contains "536870913" or
    search_filter contains "805306368" or
    search_filter contains "805306369"
| summarize count=count(), search_filters = make_set(search_filter) by DeviceName
| extend search_filter_unique_count = array_length(search_filters)
| order by search_filter_unique_count desc
```