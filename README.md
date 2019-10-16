# docker-compose-drupal

LAMP stack (Debian, Apache, MariaDB, PHP, Adminer, MailCatcher)

## Requirements
1. [Docker CE](https://download.docker.com?target=_blank) or [**Docker Toolbox**](https://github.com/docker/toolbox/releases?target=_blank) (Virtualbox)

1. [Git](https://git-scm.com/?target=_blank) (optional)

## Usage

1. Enable CPU virtualization technology in BIOS.

    - Enable Hyper-V technology in operatin system (Docker CE).
    - Disable Hyper-V technology in operatin system (Docker Toolbox and Windows only).
      
1. Clone or download and extract [docker-compose-drupal](https://github.com/vavyskov/docker-compose-drupal/archive/master.zip?target=_blank) repository:
        
       git clone https://github.com/vavyskov/docker-compose-drupal.git

1. See `.env` file.

1. Open the terminal, navigate to the directory containing the file `docker-compose.yml` and run command:

       docker-compose up -d
             
    Other commands:
    
    - `docker-compose stop` (stop containers)
    - `docker-compose start` (start containers)
    - `docker-compose down` (destroy containers)
    
1. Open the web browser:

    **Web**:
    - URL: `localhost` or `192.168.99.100` (Docker Toolbox)
    
    **SSH**
    - Port: `2202`
    - User: `www-data`
    - Password: `www-data`
    - **Edit directory** `/var/www/html` as you needed

    **Adminer**:
    - URL: `localhost:8080` or `192.168.99.100:8080` (Docker Toolbox)
    - Server: `mariadb` or `postgres`
	- User: `drupal`
	- Password: `drupal`
	- Database: `drupal`
	
	**Mailcatcher** displays sent emails:
	- URL: `localhost:1080` or `192.168.99.100:1080` (Docker Toolbox)

1. Optional configure your system `hosts` file:

	- `127.0.0.1 devel.example.com drupal.loc` (Docker CE)
	- `192.168.99.100 devel.example.com drupal.loc` (Docker Toolbox)

	Path:
    - Linux: `/etc/hosts`
	- macOX: `/private/etc/hosts`
	- Windows: `C:\Windows\System32\drivers\etc\hosts`

## Note

- Skype (Windows): Go to Tools → Options → Advanced → Connections and uncheck the box use port 80 and 443 as alternative.

## ToDo

Send a test e-mail:
- php ./test/send-mail.php

Samba:
- port: 4451
- user: drupal
- password: drupal
