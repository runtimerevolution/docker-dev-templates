# Docker Dev Templates

## Description

This repository purpose is to provide ready to use docker templates to provision development machines.
For a vagrant equivalent, please check https://github.com/runtimerevolution/vagrant-dev-templates

## Install Dependencies

* Install docker
    * https://docs.docker.com/engine/installation/mac/#/docker-for-mac
* Install [docker-sync](http://docker-sync.io)
    * `gem install docker-sync`
    * `brew install unison`
    * `easy_install pip && pip install macfsevents`

## Usages

* Copy docker-compose.yml, docker-sync.yml and Dockerfile to your project folder.

* Replace:
* <appname> placeholder by your app name. Use a simple name.
* <your name> placeholder by your name.

* Build the project docker image
    * `docker build ./ -t <appname>` or `docker-compose build web`

### Workflow

* Start docker-sync to enable fast file syncing between host and the development containers
    * `docker-sync-daemon start`
    * Run `docker-sync-daemon stop` to stop
* Start docker-compose
    * Execute `docker-compose up -d` to start on services in the background.
    * Execute `docker-compose up -d service_name [service_name 2]` to start one or more specific containers in the background.
* Execute any command line on one of the containers:
    * `docker-compose run --rm <service_name> <command to be executed>`
    * e.g:
        * `docker-compose run --rm web bundle install`
        * `docker-compose run --rm -e RAILS_ENV=test web bundle exec rake db:create db:migrate`
        * `docker-compose run --rm web bash`
* Stop developing for the day.
    * Stop docker containers with `docker-compose stop`
    * Stop docker-sync with `docker-sync-daemon stop`
* Stop developing and cleanup
    * Stop and delete docker containers with `docker-compose down -v`
    * Stop docker-sync with `docker-sync-daemon stop`
    * Delete docker-sync containers with `docker-sync clean`
* Debug with pry on a running container
    * Fetch the running container id with `docker ps` (hint: search for the container command)
    * Attach to docker container using `docker attach <container id>`
    * Exit with `ctrl-p ctrl-d` (ctrl-c will kill the container)
    * Check for more info [here](http://www.chris-kelly.net/2016/07/25/debugging-rails-with-pry-within-a-docker-container/)
* Restart a docker-container
    * `docker-compose restart <container name>`
* For more info on how this is done, read this [awesome article](https://revs.runtime-revolution.com/setting-up-a-simple-rails-development-environment-with-docker-for-fun-and-profit-71b8aa0d33c1#.2mjte0i8r)

### Troubleshoot
* If the web container fails to start and the error messages states that puma server.pid file exists run the follwing command
    * `docker-compose run --rm web rm /app/tmp/pids/server.pid`

## Roadmap

* Provide more containers examples
* Improve environment variables usage (use .env files?)
* Provide helper tools to easy up development workflow

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/runtimerevolution/vagrant-dev-templates.
