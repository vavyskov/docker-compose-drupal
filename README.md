# docker-compose-drupal

Content:
- Drupal stack
- Traefik router

## Requirements
1. [Docker CE](https://docs.docker.com/get-docker/?target=_blank) or [**Docker Toolbox**](https://github.com/docker/toolbox/releases?target=_blank) (Virtualbox)

1. [Git](https://git-scm.com/?target=_blank) (optional)

## Usage

1. Enable CPU virtualization technology in BIOS.

    - Enable Hyper-V technology in operatin system (Docker CE).
    - Disable Hyper-V technology in operatin system (Docker Toolbox and Windows only).
      
1. Clone or download and extract [docker-compose-drupal](https://github.com/vavyskov/docker-compose-drupal/archive/master.zip?target=_blank) repository:
        
       git clone https://github.com/vavyskov/docker-compose-drupal.git

1. See `project\README.md`

1. See `traefik\README.md`

## Note

- Skype (Windows): Go to Tools → Options → Advanced → Connections and uncheck the box use port 80 and 443 as alternative.
