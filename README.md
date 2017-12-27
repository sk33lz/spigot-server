# spigot-server
A spigot Minecraft server built in a docker container with volumes mapped to the local filesystem.

## Server Quickstart

Get started with some defaults out of the box with the following command.

    docker run \
        -it \
        --name spigot-server \
        -d \
        -v path/to/dir/minecraft-files:/opt/minecraft \
        -v /path/to/dir/minecraft-data:/var/lib/minecraft \
        -p 0.0.0.0:25565:25565 \
        -e DEFAULT_OP=notch \
        -e MINECRAFT_EULA=true \
        -e MINECRAFT_VERSION=1.12.2 \
        -e MOTD='A Spigot Minecraft Server' \
        -e MAX_PLAYERS=10 \
        sk33lz/spigot-server:latest

## Start a Server with Rcon

Rcon is disabled by default as it is a security risk for your server if not secured properly.

Replace `DEFAULT_OP=notch` with your Minecraft username.

Add `-e ENABLE_RCON=true \` to the docker run command to enable rcon on the server.

You will also need to add an rcon.password with `-e RCON_PASSWORD=CHANGE_ME! \`

Replace `CHANGE_ME!` in the previous statement and the example code below with a unique very secure password.

Use https://www.grc.com/passwords.htm to generate a unique very secure password.

    docker run \
        -it \
        --name spigot-server \
        -d \
        -v path/to/dir/minecraft-files:/opt/minecraft \
        -v /path/to/dir/minecraft-data:/var/lib/minecraft \
        -p 0.0.0.0:25565:25565 \
        -e DEFAULT_OP=notch \
        -e MINECRAFT_EULA=true \
        -e MINECRAFT_VERSION=1.12.2 \
        -e ENABLE_RCON=true \
        -e MOTD='A Spigot Minecraft Server' \
        -e MAX_PLAYERS=10 \
        -e RCON_PASSWORD=CHANGE_ME! \
        sk33lz/spigot-server:latest

## View Recent Server Logs

Use the following command to view the latest logs printed from your server's docker container.

    docker logs -f spigot-server

Press ctrl+c to exit the docker logs function.