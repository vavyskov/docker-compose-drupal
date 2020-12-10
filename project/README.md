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
        - Docker CE: `127.0.0.1:8083` or `localhost:8083`
        - Docker Toolbox: `192.168.99.100:8083`
        - Traefik (hosts): `project.example.com`

   **Adminer**:
    - URL:
        - Docker CE `127.0.0.1:8084` or `localhost:8084`
        - Docker Toolbox:: `192.168.99.100:8084`
        - Traefik (hosts): `project.example.com/adminer`
    - MySQL/MariaDB:
        - Server: `mariadb`
        - User: `mariadb`
        - Password: `mariadb`
        - Database: `mariadb`
    - PostgreSQL:
        - Server: `postgres`
        - User: `postgres`
        - Password: `postgres`
        - Database: `postgres`

   **Mailcatcher** displays sent emails:
    - URL: 
        - Docker CE: `127.0.0.1:1081` or `localhost:1081`
        - Docker Toolbox:: `192.168.99.100:1081`
        - Traefik (hosts): `mailcatcher.example.com`

1. SSH (SFTP)
    - Host:
        - Docker CE: `127.0.0.1` or `localhost`
        - Docker Toolbox: `192.168.99.100`
        - Traefik (hosts): `project.example.com`
    - Port: `2222`
    - User: `user`
    - Password: `password`
    - Example command: `ssh -p 2222 user@192.168.99.100`
    - **Edit the directory** `/var/www/html` and `/var/www/html/public` as you needed.

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

    - `127.0.0.1 project.example.com mailcatcher.example.com` (Docker CE)
    - `192.168.99.100 project.example.com mailcatcher.example.com` (Docker Toolbox)

   Path:
    - Linux: `/etc/hosts`
    - macOX: `/private/etc/hosts`
    - Windows: `C:\Windows\System32\drivers\etc\hosts`

## Note

Drupal 7 (handmade installation):
- wget https://ftp.drupal.org/files/projects/drupal-7.77.zip
- unzip drupal-7.77.zip

Last version of Drupa 7:
- composer create-project --no-install drupal-composer/drupal-project:7.x-dev html