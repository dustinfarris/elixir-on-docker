FROM elixir:1.5.2

RUN apt-get update && apt-get install -y inotify-tools

ARG CONTAINER_USER='elixir'

ARG APP_DIR=/home/"${CONTAINER_USER}"/app

# RUN useradd -m -u 1000 -s /usr/bin/bash "${CONTAINER_USER}"

# USER "${CONTAINER_USER}"

WORKDIR "${APP_DIR}"

RUN mix local.hex --force && mix local.rebar --force
# TODO get + build deps

COPY . ./

# Cleartext port
EXPOSE 8080
# Secure port
EXPOSE 8443
# Wobserver port
EXPOSE 4001

CMD ["sh", "bin/start"]
