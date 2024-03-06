FROM elixir:1.16-otp-26
LABEL maintainer="Klaas Jan Dijksterhuis"

ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID

# Create a user
RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME

RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends \
        ca-certificates \
        inotify-tools \
        sqlite3 \
        curl \
        git

# Remove or comment out to use root user
USER $USERNAME

# Install Hex and the Phoenix application generator
RUN mix local.hex --force \
    && mix archive.install hex phx_new --force
