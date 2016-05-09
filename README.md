This docker image provides a Tekkit Legend (Minecraft) Server that will automatically download the latest stable
version at startup.

To simply use the latest stable version, run

    docker run -d -p 25565:25565 --name mc rizbe/tekkit-legend

where the standard server port, 25565, will be exposed on your host machine.

If you want to serve up multiple Minecraft servers or just use an alternate port,
change the host-side port mapping such as

    docker run -p 25566:25565 ...

will serve your Minecraft server on your host's port 25566 since the `-p` syntax is
`host-port`:`container-port`.

Speaking of multiple servers, it's handy to give your containers explicit names using `--name`, such as

    docker run -d -p 25565:25565 --name mc rizbe/tekkit-legend

With that you can easily view the logs, stop, or re-start the container:

    docker logs -f mc
        ( Ctrl-C to exit logs action )

    docker stop mc

    docker start mc

## Interacting with the server

In order to attach and interact with the Minecraft server, add `-it` when starting the container, such as

    docker run -d -it -p 25565:25565 --name mc rizbe/tekkit-legend

With that you can attach and interact at any time using

    docker attach mc

and then Control-p Control-q to **detach**.
