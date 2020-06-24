Stop the web server

```
root@webserver:~# service lsws stop
```
Run certbot to issue another certificate

```
root@webserver:~# certbot certonly
```
```
Choose the method you want to authenticate your domain ownership with the ACME CA. I chose option 1 "Spin up a temporary webserver (standalone)" which is the reason that we stopped the webserver in the first instance as we cannot have two webservers trying to use the same port (s) at the same time.

How would you like to authenticate with the ACME CA?
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
1: Spin up a temporary webserver (standalone)
2: Place files in webroot directory (webroot)
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Select the appropriate number [1-2] then [enter] (press 'c' to cancel): 1

Now type in the domain name(s) that you need the certificate to be issued for

Please enter in your domain name(s) (comma and/or space separated)  (Enter 'c'
to cancel): example.com

Certbot will go through and do it's stuff and create the certificate(s) that you need and it will tell you where it has placed the certificate files.

Cert is due for renewal, auto-renewing...
Renewing an existing certificate
Performing the following challenges:
http-01 challenge for example.com
Waiting for verification...
Cleaning up challenges

IMPORTANT NOTES:
 - Congratulations! Your certificate and chain have been saved at:
   /etc/letsencrypt/live/example.com/fullchain.pem
   Your key file has been saved at:
   /etc/letsencrypt/live/example.com/privkey.pem
   Your cert will expire on 2019-XX-XX. To obtain a new or tweaked
   version of this certificate in the future, simply run certbot
   again. To non-interactively renew *all* of your certificates, run
   "certbot renew"
 - If you like Certbot, please consider supporting our work by:

   Donating to ISRG / Let's Encrypt:   https://letsencrypt.org/donate
   Donating to EFF:                    https://eff.org/donate-le

Once the certs have been obtained we are going to start up OpenLiteSpeed again
```

```
root@webserver:~# service lsws start
```