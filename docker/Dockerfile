ARG CADDY_VERSION
FROM caddy:${CADDY_VERSION}-builder-alpine AS app_caddy_builder

RUN xcaddy build \
	--with github.com/caddy-dns/cloudflare \
	--with github.com/lucaslorentz/caddy-docker-proxy/v2@v2.7.0

FROM caddy:${CADDY_VERSION}-alpine

WORKDIR /srv/app

COPY --from=app_caddy_builder --link /usr/bin/caddy /usr/bin/caddy
