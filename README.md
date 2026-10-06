# opencloud-quadlet

🎼 This repository provides podman Quadlet configurations for deploying OpenCloud in various environments.

Heavily inspired from [opencloud-compose](https://github.com/opencloud-eu/opencloud-compose)

> [!WARNING]
> In early development

Everything runs inside one Podman pod (`opencloud.pod`). Because the containers share a network namespace, they reach each other over `127.0.0.1` and need no internal networking setup. The pod only publishes ports on localhost, so a reverse proxy on the host is expected to handle TLS and public traffic.

OpenCloud itself (`opencloud.container`) is the only service enabled by default. Optional add-ons live in `addons/` and are switched on with systemd drop-ins in `opencloud.container.d/`, which ship disabled. To enable it remove the `.disabled` at the end of the filename
