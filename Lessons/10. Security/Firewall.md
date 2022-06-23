Notes: Do nmap scans before this

Firewall/NAT tab

1. Add Ruleset
   1. Name it ISLAND
2. Click `Actions` beside ruleset and click `edit`
   1. On Rules tab, enter:
      1. DNS
         1. Accept
         2. Both TCP/UDP
         3. Dest 10.226.x.10
         4. port 53
      2. Email
         1. Accept
         2. Both TCP/UDP
         3. Destin 10.226.x.15
         4. port 25 
      3. www
         1. Accept
         2. Both TCP/UDP
         3. Destin 10.226.x.20
         4. port 80
      4. Save
   2. On interface tab
      1. Interface is `eth4`
      2. `In` for direction
3. Test the rules and realize it broke everything
   1. Add Established inbound rule
      1. Accept
      2. All Protocols
      3. Advanced Tab: `Established`