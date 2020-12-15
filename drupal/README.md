# Project stack for Drupal

Content:
- Linux
- (E)Nginx
- MariaDB/PostgreSQL
- PHP
- Mailcatcher
- Adminer

## Quick start

1. See `.env` file.

1. Open the terminal, navigate to the directory containing the file `docker-compose.yml` and run commands:

       docker network create backend_network
       docker network create frontend_network
       docker-compose up -d

   Other commands:

    - `docker-compose stop` (stop containers)
    - `docker-compose start` (start containers)
    - `docker-compose down` (destroy containers)

1. Open the web browser:

   **Web**:
    - URL:
        - Docker CE: `localhost:8083` or `127.0.0.1:8083`
        - Docker Toolbox: `192.168.99.100:8083`
        - Traefik (hosts): `drupal.example.com`

   **Adminer**:
    - URL:
        - Docker CE: `localhost:8084` or `127.0.0.1:8084`
        - Docker Toolbox: `192.168.99.100:8084`
        - Traefik (hosts): `adminer.example.com`
    - MySQL/MariaDB:
        - Host and port: 
            - Docker CE: `localhost:3308` or `127.0.0.1:3308`
            - Docker Toolbox: `192.168.99.110:3308`
        - User: `drupal`
        - Password: `drupal`
        - Database: `drupal`
    - PostgreSQL:
        - Host and port:
            - Docker CE: `localhost:5434` or `127.0.0.1:5434`
            - Docker Toolbox: `192.168.99.110:5434`
        - User: `drupal`
        - Password: `drupal`
        - Database: `drupal`

   **Mailcatcher** displays sent emails:
    - URL: 
        - Docker CE: `localhost:1081` or `127.0.0.1:1081`
        - Docker Toolbox:: `192.168.99.100:1081`
        - Traefik (hosts): `mailcatcher.example.com`

1. SSH (SFTP)
    - Host:
        - Docker CE: `localhost` or `127.0.0.1`
        - Docker Toolbox: `192.168.99.100`
        - Traefik (hosts): `drupal.example.com`
    - Port: `2222`
    - User: `user`
    - Password: `password`
    - Example command: `ssh -p 2222 user@192.168.99.100`
    - **Edit the directory** `/var/www/html` and `/var/www/html/public` as you needed.

1. SMTP
   - Host and port:
      - Docker CE: `localhost:1026` or `127.0.0.1:1026`
      - Docker Toolbox: `192.168.99.100:1026`

1. Optionally install **Drush** (is included in the Drupal composer installation) with Composer and then run command:

       composer global require drush/drush
       (composer global require drush/drush:8)
   
       echo 'export PATH="$HOME/.composer/vendor/bin:$PATH"' >> ~/.bashrc
   
       echo 'alias drush="~/.composer/vendor/bin/drush"' >> ~/.bashrc
       (echo 'alias drush="~/html/vendor/bin/drush"' >> ~/.bashrc)
       
       source ~/.bashrc

    Basic command:

       drush status

1. Install **Drupal Console** with Composer and then run commands:

       composer require drupal/console:~1.0 --prefer-dist --optimize-autoloader

       echo 'export PATH="$HOME/.composer/vendor/bin:$PATH"' >> ~/.bashrc
   
       echo 'alias drupal="~/.composer/vendor/bin/drupal"' >> ~/.bashrc
       (echo 'alias drupal="~/html/vendor/bin/drupal"' >> ~/.bashrc)
       
       source ~/.bashrc 

    Basic commands:
   
       drupal site:status
       drupal site:statistics

1. Optionally configure your system `hosts` file:

    - Docker CE: `127.0.0.1 drupal.example.com adminer.example.com mailcatcher.example.com`
    - Docker Toolbox: `192.168.99.100 drupal.example.com adminer.example.com mailcatcher.example.com`

   Path:
    - Linux: `/etc/hosts`
    - macOX: `/private/etc/hosts`
    - Windows: `C:\Windows\System32\drivers\etc\hosts`

## Note

Last version:
- Drupal 9: `composer create-project drupal/recommended-project html --no-install`
- Drupal 8: `composer create-project drupal/recommended-project:8.9.x-dev html --no-install`
- Drupal 7: `composer create-project drupal-composer/drupal-project:7.x-dev html --no-install`

## Sending e-mails

Docker CE (SMTP port 1026):
   - ???

Docker Toolbox (SMTP port 1026):
   - Web: OK
   - Wordpress: OK
   - Drupal require module https://www.drupal.org/project/smtp
