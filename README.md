# ksynth-agent-docker

Notes on running dockerized ksynth-agent.

Sensitive data goes into `.env` file and those are referenced into the compose file as variables

Environment variables exposed into the ksynth container go into `ksynth-agent.env` file.

### `docker-compose.yml`
Spins up the ksynth container mounting the `./data/ksynth-agent` folder to the proper place in order to preserve additional files needed and the agent identity in the portal

### `docker-compose-2nics.yml`
Spins up two ksynth containers bound to two different network cards, i.e. a wired and a wireless NIC in order to perform independent tests.
The network driver used here is a macvlan bridge to the hosts physical adapters.  Static IPs are assigned to the containers, or the `ip_range` knob can be used to assign from a custom pool.
Bind mounts are `./data/wired` and `./data/wireless` respectively.
