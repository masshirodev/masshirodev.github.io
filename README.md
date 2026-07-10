# masshiro.pro

Static site for `masshiro.pro`, served by Caddy in Docker.

## Run locally

```sh
docker compose up --build
```

The site listens on:

- `http://localhost`
- `https://localhost`

## Deploy on the VPS

Point these DNS records at the VPS IPv4 address first:

```text
A  @    YOUR_VPS_IPV4
A  www  YOUR_VPS_IPV4
```

Then on the VPS:

```sh
sudo pacman -Syu --needed docker docker-compose
sudo systemctl enable --now docker
sudo usermod -aG docker masshiro
```

Log out and back in so the `docker` group applies, then:

```sh
git clone https://github.com/masshirodev/masshirodev.github.io.git
cd masshirodev.github.io
docker compose up -d --build
```

Caddy automatically requests and renews HTTPS certificates for `masshiro.pro` and `www.masshiro.pro`.
