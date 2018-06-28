# Setup Visual Studio Code for XDebug in Docker container

I was looking for a solution in which I would not have to hard code the docker host ip-address. Follow these steps to set it up for your container.

Looking for a [LAMP or development stack](https://github.com/RobinWijnant/docker-compose-dev-stack)? I have created mine with this Xdebug settings.

## Configuration

### php.ini [container]

Docker translates `host.docker.internal` in the ip-address of the host machine.

```ini
[XDebug]
xdebug.remote_enable = 1
xdebug.remote_autostart = 1
xdebug.remote_host=host.docker.internal
```

### .vscode/launch.json [host]

Change the pathMapping to your needs

```Json
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "XDebug Dev Stack",
            "type": "php",
            "request": "launch",
            "port": 9000,
            "pathMappings": {
                "/var/www": "${workspaceRoot}/www"
              }
        }
    ]
}
```
