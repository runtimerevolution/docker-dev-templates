# Changelog

## 0.2.0
* Support for changes introduced and recommended on docker-sync 0.3.0 and 0.4.x
    * Update docker-compose docker-sync volumes to use :nocopy. More info [here](https://github.com/EugenMayer/docker-sync/wiki/2.-Configuration#why-nocopy-is-important)
    * Remove deprecated docker-sync 'dest' configuration. More info [here](https://github.com/EugenMayer/docker-sync/wiki/1.2-Upgrade-Guide#dest-has-been-removed)
    * Update docker-sync sync_strategy to use native_osx.
    * Update Readme with the new docker-sync daemon command
* Update docker-sync configuration to add back the tmp and sass-cache folders to avoid things like assets full recompilation on when rebuilding a development container
* Update docker-sync sync_host_ip and delete unnecessary sync_host_port setting

## 0.1.0
First release
