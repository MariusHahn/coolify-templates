# coolify-templates

## Add Passbolt admin user 

Use this command from inside the passbolt container to setup the admin user

```bash
su -m -c "/usr/share/php/passbolt/bin/cake \
    passbolt register_user \
    -u you@your_oragnisation_mail.com \
    -f FIRST_NAME \
    -l LAST_NAME \
    -r admin" \
    -s /bin/sh www-data
```