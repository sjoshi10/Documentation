# Set up FreeIPA


```
yum install ipa-server ipa-server-dns -y

ipa-server-install -a <password> --hostname=<FreeIPA hostname> -r <DNS ZONE> -p <password> -n <DNS ZONE> -U --setup-dns --no-forwarders
```
