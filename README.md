# bastille-letsencrypt
This Bastille Template installs ACME.SH in a separate jail.
The configuration is copied from ``/usr/local/etc/git_config/acme.sh/account.conf``.
The certificates will be written to host system using mount:
```sh
MOUNT /werzel/certificates var/db/acme/certs nullfs rw 0 0
```

### INWX parameters
INWX offers an xmlrpc api with your standard login credentials, set them like so:
```sh
export INWX_User="yourusername"
export INWX_Password="password"
```
Then you can issue your certificates with:
```sh
acme.sh --issue --dns dns_inwx -d example.com -d www.example.com
```
The INWX_User and INWX_Password settings will be saved in ~/.acme.sh/account.conf and will be reused when needed.

If your account is secured by mobile tan you have also defined the shared secret.
```sh
export INWX_Shared_Secret="shared secret"
```
You may need to re-enable the mobile tan to gain the shared secret.

#### Bla
In order to automatically renew the certificates, add this line to
/etc/periodic.conf:

    weekly_certbot_enable="YES"


    certbot certonly --standalone -d

    certbot certonly -a dns-inwx -d sub.domain.tld -d *.wildcard.tld