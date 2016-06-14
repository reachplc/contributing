# Server Setup

## Media Temple

### SSH into our account.

### Give Codeship access to this site

Add Codeship public key to `vim ~/.ssh/authorized_keys`. *Adding a heading to the key will help identify which key relates to a project.*

### Create deployment folders

Create `/releases`, `/shared` and `/config` directories at the root level of this site (the same level above the `/html` folder).

```
mkdir ~/domains/<folder name eg, example.com>/{releases,shared,config}
```

Inside the `/shared/` folder you will need to create any folder that will be shared across all releases. For a WordPress project these may be `/shared/media/` and `/shared/languages/`.

### Install Composer and dependencies

Change into the projects root directory:

```
cd ~/domains/<folder name eg, example.com>/
```

Run the following commands to install Composer:

```
curl -s https://getcomposer.org/installer | php -d allow_url_fopen=1 -d suhosin.executor.include.whitelist=phar
php -d memory_limit=512M -d allow_url_fopen=1 -d suhosin.executor.include.whitelist=phar composer.phar
```

Install phpdotenv by running the following command.
This allows us to set custom global variables for things like database usernames and passwords. Keeping them safely outside of our committed code.

```
php -d memory_limit=512M -d allow_url_fopen=1 -d suhosin.executor.include.whitelist=phar composer.phar require vlucas/phpdotenv
```

### Configure the project

Create your `.env` file containing any global variables you might need such as `ENV=production`.

```
touch .env
```

Add any configuration files to the `/config/` folder needed for the projust. For a WordPress project these might be `/config/application.php`
