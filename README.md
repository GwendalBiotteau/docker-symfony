# Docker Symfony

By [Gwendal BIOTTEAU](https://gwendalbiotteau.fr)

**Containers available:**

| Service    | Container name            | Info                                          |
| ---------- | ------------------------- | --------------------------------------------- |
| php        | (project-name)-php        | Based on [phpdocker.io](https://phpdocker.io) |
| nginx      | (project-name)-nginx      |                                               |
| mysql      | (project-name)-mysql      |                                               |
| adminer    | (project-name)-adminer    |                                               |
| phpmyadmin | (project-name)-phpmyadmin |                                               |
| mailhog    | (project-name)-mailhog    |                                               |

**Additional tools:**

| Name   | Description                                 |
| ------ | ------------------------------------------- |
| Xdebug | Xdebug configuration for Visual Studio Code |

## Install

The first thing to do is to include this repository into your Symfony project and set the `.env.local` variables to fit your project requirements. (Theses are just the required variables used by Docker, you will probably need to use your own variables in addition to those present in this repo).

You can now build the Docker containers (use Makefile commands if Make is installed on your computer) :  
`make docker_build`  or `docker-compose --env-file ./.env.local build` (it might take a while, so be patient :))

Then run the containers to start the project:  
`make start` or `docker-compose --env-file ./.env.local up -d`

*Note: it is also possible for Linux users to use this command to stop apache and mysql services before running:*  
`make full-start` or `sudo systemctl stop apache2.service && sudo systemctl stop mysql.service && docker-compose --env-file ./.env.local up -d`

**Your symfony project is no available and running on `http://localhost` url (`http://127.0.0.1`)!**

## Use containers

You can access these services from the following ports:
- phpMyAdmin: `port 81` (`http://localhost:81`).
- Adminer: `port 8182` (`http://localhost:8182`).
- Mailhog: `port 82` (`http://localhost:82`).

In order to run commands in the container with docker config such as NPM or Composer, you need to access the docker bash container with:  
`make bash` or `docker-compose --env-file ./.env.local exec php zsh`

## Thanks

That's it for this project, feel free to send me a pull request in order to improve this Docker boilerplate and of course adapt it to your needs! :)