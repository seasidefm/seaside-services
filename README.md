## Seaside Services

Random Docker services that keep the SeasideAPI running!

### Directory
- `nginx-confs`: NGINX config files for rtmp and other "high level" containerized applications.
- `rtmp-auth`: dockerfile and config for the RTMP Authentication module. runs in parralel to rtmp-enabled nginx image to allow authenticated OBS or GoPro streams.
- `volumes`: misc volume mount folder for convenience purposes.

### Running
- Populate any services `.env` files (none at the moment).
- Run `docker-compose up` to ensure things work or `docker-compose up -d` for production.

### Notes to consumers (hello future me!)
- When consuming an RTMP stream via OBS or other "re-broadcaster", do NOT use the HLS url. That URL adds 5-6 seconds of delay due to ffmpeg conversion to HLS and will create pain for your viewers. Use the `rtmp` url for this purpose as it doesn't even add a second of delay if done properly.
    ```shell
    rtmp://<server hostname>/live/<service>
    ```
- When do I use an HLS stream then? Good question! If you want your stream to be consumed by the end user (like twitch), or are using the stream in an environment without direct access to `ffmpeg`.
    ```shell
    https://<server hostname>/live/<service>_hd.m3u8
    ```
