# Tailscale in Docker without elevated privileges

See associated blog post: <https://asselin.engineer/tailscale-docker>

**Set the TAILSCALE_AUTH_KEY with your own ephemeral auth key**: <https://login.tailscale.com/admin/settings/keys>

## docker-compose

The examples detailed below are in the docker-compose folder.

By default, no state is saved. The nodes are removed from the network when the tailscale container is terminated. This means the ip address is never the same.
The `stateful-example` does save the tailscale node state to a docker volume.

Requirements:
- [docker-compose](https://docs.docker.com/compose/install/)

Usage:
````bash
export TAILSCALE_AUTH_KEY="your-key"
# set which project is used
export PROJECT_DIRECTORY="docker-compose/simple-example"
# Sart with rebuild if necessary:
docker-compose --project-directory=${PROJECT_DIRECTORY} up -d --build
# Show logs and tail (follow):
docker-compose --project-directory=${PROJECT_DIRECTORY} logs --follow
# Stop:
docker-compose --project-directory=${PROJECT_DIRECTORY} down
````
