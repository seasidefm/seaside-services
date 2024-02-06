## Seaside Services

Random Docker services that keep the SeasideAPI running!

### Directory
- `nginx-confs`: NGINX config files for rtmp and other "high level" containerized applications.
- `rtmp-auth`: dockerfile and config for the RTMP Authentication module. runs in parralel to rtmp-enabled nginx image to allow authenticated OBS or GoPro streams.
- `volumes`: misc volume mount folder for convenience purposes.

### Running
- Populate any services `.env` files (none at the moment).
- Run `docker-compose up` to ensure things work or `docker-compose up -d` for production.