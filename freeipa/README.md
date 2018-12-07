# Set up FreeIPA

### Set up FreeIPA server
```
yum install ipa-server ipa-server-dns -y

firewall-cmd --permanent --add-port=80/tcp
firewall-cmd --permanent --add-port=88/tcp
firewall-cmd --permanent --add-port=389/tcp
firewall-cmd --permanent --add-port=443/tcp
firewall-cmd --permanent --add-port=888/tcp
firewall-cmd --permanent --add-port=88/udp
firewall-cmd --reload

ipa-server-install -a <password> --hostname=<FreeIPA hostname> -r <DNS ZONE> -p <password> -n <DNS ZONE> -U --setup-dns --no-forwarders
```

### Modify FreeIPA Admin Group rules
We want our admin users to be able to run sudo commands. Following are steps to configure sudo for admin users. 
 
1. Put freeipa into your browser. 
2. Policy > Sudo > Sudo Rules
3. Click on "+ Add" to add new Sudo rule. 
4. Click on new created Rule name and modify the default rules. 
5. Who: Click on "Specified Users and Groups". Under "User Groups", click "+ Add" and add admins group. 
6. Access this Host: Click on "Any Host". Becareful, this will give this group sudo access to all hosts. 
7. Run Commands: Click on "Any Command".
8. Click save



### Set up FreeIPA Client
```
ipa-client-install --server test.fios-router.home --domain test.fios-router.home  -w password --principal admin
authconfig --enablemkhomedir --update
```
### Run LDAP search on FreeIPA
`ldapsearch -x -h freeipa.example.com -b dcexample,dc=com uid=<Username>`
