# Server Setup

## Media Temple

### SSH into our account.

### Give Codeship access to this site

Add Codeship public key to `vim ~/.ssh/authorized_keys`. *Adding a heading to the key will help identify which key relates to a project.*

### Create deployment folders

Create `/releases` and `/shared` directories at the root level of this site (the same level above the `/html` folder).

### Install Composer and dependencies

In the sites root folder. Run the following commands to install Composer:

```
curl -s https://getcomposer.org/installer | php -d allow_url_fopen=1 -d suhosin.executor.include.whitelist=phar
php -d memory_limit=512M -d allow_url_fopen=1 -d suhosin.executor.include.whitelist=phar composer.phar
```

Install phpdotenv by running the following command.
This allows us to set custom global variables for things like database usernames and passwords. Keeping them safely outside of our committed code.

```
php -d memory_limit=512M -d allow_url_fopen=1 -d suhosin.executor.include.whitelist=phar composer.phar require vlucas/phpdotenv
```

Create your `.env` file containing any global variables you might need such as `ENV=production`.
