# opencloud-quadlet

🎼 This repository provides podman Quadlet configurations for deploying OpenCloud in various environments.

Heavily inspired from [opencloud-compose](https://github.com/opencloud-eu/opencloud-compose)

> [!WARNING]
> In early development
>
> Requires **podman 5.5+**

Everything runs inside one Podman pod (`opencloud.pod`). Because the containers share a network namespace, they reach each other over `127.0.0.1` and need no internal networking setup. The pod only publishes ports on localhost, so a reverse proxy on the host is expected to handle TLS and public traffic.

OpenCloud itself (`opencloud.container`) is the only service enabled by default. Optional add-ons live in `addons/` and are switched on with systemd drop-ins in `opencloud.container.d/`, which can be symlinked from `addons/drop-ins`.

## Configuration

Copy `opencloud.env.example` to `opencloud.env` and adjust it. Everything you must change before OpenCloud can start is in this one file, so you don't have to hunt through the unit files. Because it's not tracked by git, `git pull` won't conflict with your values. When you enable an add-on, uncomment its section there too.
