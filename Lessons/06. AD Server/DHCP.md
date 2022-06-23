### DHCP

1. Server Manager
   1. Add Role
2. Add Roles and Features Wizard
   1. Installation Type
      1. Role-based or feature based
   2. Server selection
      1. Select a server from the server pool
      2. Pick only server there
      3. Next
   3. Server Roles
      1. DHCP Server
      2. Add Features
      3. Next
   4. Features
      1. Defaults
      2. Next
   5. DHCP Server
      1. Next
   6. Confirmation
      1. Check box 'Restart destination server automatically if required'
      2. Install
   7. Close
3. Finish DHCP config
   1. Server manager
      1. DHCP on the left
      2. Click the Flag at the top and click 'Complete DHCP Configuration'
      3. Click next
      4. Click the top radio button with `ISLAND\Administrator` specified
      5. Click Close
4. Configure DHCP
   1. Server Manager
      1. Click tools -> DHCP
   2. DHCP Tool
      1. Expand dc.ISLAND.jp.lan
      2. Right-click IPv4 and click 'New Scope'
   3. New Scope Wizard
      1. Click next
      2. Name it ISLAND & click next
      3. IP Address range
         1. For start IP, use 10.226.x.50
         2. For end IP, use 10.226.x.200
         3. For length, specify 24 (which changes mask to 255.255.255.0)
         4. Click next
      4. Accept defaults on Exclusions & click next
      5. Accept defaults on Lease duration & click next
      6. Leave 'Yes' checked for Configure DHCP options & click next
      7. For router, enter 10.226.x.1 and click Add, then Next
      8. For Domain Name and DNS Server, accept defaults and click next
      9. Click next on WINS servers
      10. Leave 'Yes' to activate scope and click next
      11. Click Finish
   4. 