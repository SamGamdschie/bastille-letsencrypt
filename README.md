# bastille-letsencrypt


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