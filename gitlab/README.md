# Setup Gitlab

### Install Gitlab on Centos7
https://about.gitlab.com/install/#centos-7

### SSL 

```
external_url "<>"
nginx['ssl_certificate'] = "/etc/gitlab/ssl/<>.crt"
nginx['ssl_certificate_key'] = "/etc/gitlab/ssl/<>.key"
```




### LDAP
```
gitlab_rails['ldap_enabled'] = true
gitlab_rails['ldap_servers'] = YAML.load <<-'EOS'
  main: # 'main' is the GitLab 'provider ID' of this LDAP server
    label: 'LDAP'
    host: 'ldap_url'
    port: 389
    uid: 'uid'
    bind_dn: 'uid=<>,cn=users,cn=accounts,dc=example,dc=com'
    password: '<>'
    encryption: 'plain' # "start_tls" or "simple_tls" or "plain"
    verify_certificates: false
    base: 'dc=example,dc=com'
    attributes:
      username: ['uid']
      email: ['mail']
      name: 'displayName'
      first_name: 'givenName'
      last_name: 'sn'
EOS
```
