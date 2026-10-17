# festum/bansos

`festum/bansos` is an unofficial Docker image of [bansos-router](https://github.com/ihsan-ramadhan/bansos-router).

The image workflow checks the upstream repository's default-branch commit SHA once an hour. When that SHA has not already been published, it builds the upstream source and pushes `latest` and `sha-<commit>` tags. Tags are available only after the workflow successfully publishes them.

```sh
docker pull festum/bansos:latest
docker run -d --name bansos \
  -p 17070:17070 \
  -v bansos-data:/home/node/.bansos \
  festum/bansos:latest
```

The volume keeps the daemon's state in `/home/node/.bansos`. The container exposes port `17070` and its Docker healthcheck probes `http://127.0.0.1:17070/healthz`.
