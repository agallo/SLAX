various SLAX scripts

### requireIFdescriptions.slax

will cause commit to fail unless PHY inteface has a description
TODO: check for descriptions on any configured units with the following logic:
```
    if number of units > 1, require description on each unit
        logic-  if there is only one unit, description of the parent physical interface will suffice
                if there are multiple units, each should have a description
``` 
### requireBGPpolicy.slax

check all external BGP peers- if no policy, apply default DENY

requires `po_DEFAULT-BGP-POLICY-DENY-ALL` to be configured

script files go in `/var/db/scripts/commit` and are configured under [edit system scripts commit]
```
system{
    scripts {
        commit {
            file requireIFdescriptions.slax;
            file requireBGPpolicy.slax;
		}
	}
}
```