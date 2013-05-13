# WordPress Heroku with ClearDB


Installation
============


Create your app

    $ heroku create YOUR_APP_NAME  -s cedar -b git://github.com/iphoting/heroku-buildpack-php-tyler.git

Add a database to your app

    $ heroku addons:add cleardb:ignite


Create a new branch for any configuration/setup changes needed

    $ git checkout -b production

Copy the "wp-config.php"

    $ cp wp-config-sample.php wp-config.php

Update unique keys and salts in `wp-config.php` on lines 48-55. Wordpress can provide random values [here](https://api.wordpress.org/secret-key/1.1/salt/).

    define('AUTH_KEY',         'put your unique phrase here');
    define('SECURE_AUTH_KEY',  'put your unique phrase here');
    define('LOGGED_IN_KEY',    'put your unique phrase here');
    define('NONCE_KEY',        'put your unique phrase here');
    define('AUTH_SALT',        'put your unique phrase here');
    define('SECURE_AUTH_SALT', 'put your unique phrase here');
    define('LOGGED_IN_SALT',   'put your unique phrase here');
    define('NONCE_SALT',       'put your unique phrase here');

Commit wp-config.php

    $ git add wp-config.php
    $ git commit -m "Initial WordPress commit"

Deploy to Heroku

    $ git push heroku production:master


Switch language

    $ heroku config:add WORDPRESS_LANG=ja # ja
    $ heroku config:add WORDPRESS_LANG='' # en