# Sherlock: CrownJewel-1

## Notes

- **NTDS.dit** — New Technology Directory Services database; the primary database inside Active Directory DS (the backbone of AD)
- The attacker used `vssadmin` on the domain controller to create a shadow copy and access `NTDS.dit`
- The attacker leveraged a LOLBin (Living Off the Land Binary) utility
