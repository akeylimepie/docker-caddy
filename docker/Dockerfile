ARG CADDY_VERSION
FROM --platform=$BUILDPLATFORM caddy:${CADDY_VERSION}-builder-alpine AS builder

ARG TARGETOS
ARG TARGETARCH

# github.com/caddy-dns/cloudflare v0.2.4
# github.com/WeidiDeng/caddy-cloudflare-ip main @ 2023-11-30
RUN GOOS=$TARGETOS GOARCH=$TARGETARCH xcaddy build \
	--with github.com/caddy-dns/cloudflare@a8737d095ad5a48ca031cea6ab704057dbc2d250 \
	--with github.com/WeidiDeng/caddy-cloudflare-ip@f53b62aa13cb7ad79c8b47aacc3f2f03989b67e5

FROM caddy:${CADDY_VERSION}-alpine

WORKDIR /etc/caddy

COPY --from=builder --link /usr/bin/caddy /usr/bin/caddy
