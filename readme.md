Based on:

https://docs.docker.com/samples/wordpress/

Komma igång

1. Skapa en fork av repot
2. Kör kommandot:

    docker-compose up -d

3. När mappen "wordpress" är skapad. Lägg in en plugin-fil i wp-content/plugins.
4. För att komma igång med testning, kör:

`docker-compose exec wordpress wp scaffold plugin-tests [pluginnamn] --allow-root`

`docker-compose exec wordpress bash -c "/var/www/html/wp-content/plugins/[pluginnamn]/bin/install-wp-tests.sh wordpress_test root 'somewordpress' db latest"`

5. Ladda ner polyfill för PHPUnit och lägg i wordpress/vendor:

https://github.com/Yoast/PHPUnit-Polyfills


6. Lägg till i tests/bootstrap.php:

`define('WP_TESTS_PHPUNIT_POLYFILLS_PATH', '../../../vendor/PHPUnit-Polyfills/phpunitpolyfills-autoload.php')`

7. För att testa ditt plugin, kör:

`docker-compose exec wordpress bash -c "cd /var/www/html/wp-content/plugins/[pluginnamn]; phpunit"`

8. För att se din Wordpress-site. Gå till http://localhost:8001