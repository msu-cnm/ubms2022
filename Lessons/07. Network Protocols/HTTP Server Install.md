- To do:
  - Add CD-Rom
  - Change root PW
  - Up video RAM to 128MB
  - Change IP to .20
  - Put placeholder in /etc/sysconfig/network webserver.ISLAND.jp.lan
  - Put placeholder in /etc/hosts webserver.ISLAND.jp.lan
  - Disable SELinux

1. Import CentOS 6 OVA

2. Login with `ubms:Jurassic2022`

3. Install Virtual Box Tools

   1. Insert CD
   2. Choose `Open Autorun Prompt`
   3. Choose `run`
   4. Enter root password `Jurassic2022`
   5. When install finishes, restart machine

4. Change IP address

   ```bash
   sudo vi /etc/sysconfig/network-scripts/ifcfg-eth1
   # Modify
   IPADDR=
   GATEWAY=
   DNS1=
   DOMAIN=
   ```

5. Fix hostname
   ```bash
   sudo vi /etc/sysconfig/network
   HOSTNAME=
   
   sudo vi /etc/hosts
   
   
   ```
   
6. Start httpd service

   ```bash
   sudo service httpd start
   sudo chkconfig httpd on
   ```

7. Test locally
   ```bash
   http://127.0.0.1
   ```

8. Poke hole in firewall
   ```bash
   sudo iptables -I INPUT -p tcp -m tcp --dport 80 -j ACCEPT
   sudo iptables-save > /etc/sysconfig/iptables
   ```

9. Test remotely (from another machine)

   ```bash
   http://10.226.x.20
   ```

10. Enable drag/drop of files & drag JP website files over

11. Extract JP web files 

    ```bash
    cd Desktop
    sudo unzip JurassicWeb.zip -d /var/www/
    ```

12. Set permissions on JP Files

    ```bash
    chmod 755 /var/www/cgi-bin/test/cgi
    ```

Let them play around with the website