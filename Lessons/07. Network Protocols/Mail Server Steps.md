Follow Win10 Install up to reboot

1. Domain join
2. User: mailadmin
3. Password: Jurassic2022
4. Security Questions
   1. Pick any question
   2. Put `JP` as the answer
5. Deselect all privacy questions and click Accept
6. Cortana - Not Now
7. Install Guest Additions
8. Enable drag & drop
9. Set IP for server to 10.226.x.15/24, DNS to .10, GW .1
10. change hostname to mail and join to domain
    1. Search for `Access Work or school`
    2. Connect
    3. Join this device to a local AD domain
    4. Enter your domain name
    5. enter administrator:Aa12345
    6. For add account prompt, choose 'skip'
11. Login to server as domain admin
12. Copy hmail server & dotnet framework over to Win10
13. Install .net Framework
14. Install hmail server
    1. Pass: Aa12345

Hmail Setup

Can use this as src: http://vcloud-lab.com/entries/general/build-a-simple-email-server-for-home-lab-using-hmailserver-and-thunderbird

1. Open hMail Server Administrator
2. Choose localhost and connect (supply pass: Aa12345)
3. Click Domains on left, and Add on right
   1. Enter your domain `ISLAND.jp.lan`
   2. Click Save
4. Create accounts
   1. On the left, expand your domain
   2. Rich-click 'Accounts' on the left
   3. Click Add
   4. In address, enter `admin` to create the email `postmaster@ISLAND.jp.lan`
   5. For password, enter `Aa12345`
   6. Click Save
   7. Repeat steps 2-5 to create three more accounts
      1. mgmt
      2. helpdesk
      3. hr
5. Disable SMTP auth
   1. Settings >> Advanced >> Ip Ranges >> Internet
   2. Uncheck all boxes under 'Require SMTP authentication'
   3. Click Save

Client Setup

1. On Win10 Client, copy over Thunderbird
2. Install Thunderbird
   1. Accept all defaults, just keep clicking next/install
   2. Click Finish and keep box checked to launch thunderbird
3. Configure Thunderbird
   1. On account setup, enter:
      1. Full Name: Help Desk
      2. Email Address: helpdesk@ISLAND.jp.lan
      3. Password: Aa12345
      4. Click Done
      5. On the warning, check the box 'I understand the risks'
      6. Click Confirm
4. Get mail