FROM ubuntu:jammy

ENV DEBIAN_FRONTEND="noninteractive"

RUN apt-get update --allow-insecure-repositories && \
    apt-get install -y --allow-unauthenticated --no-install-recommends \
    # Install Zsh to use Oh My Zsh
    zsh \
    # Lean 4 needs some basic tools to install
    ca-certificates curl git wget

# Install Lean 4
ARG ELAN_INSTALLATION_SCRIPT_URL="https://raw.githubusercontent.com/leanprover/elan/master/elan-init.sh"
RUN wget --no-check-certificate \
        -O /tmp/elan-init.sh \
        ${ELAN_INSTALLATION_SCRIPT_URL} && \
    bash /tmp/elan-init.sh -y && \
    rm /tmp/elan-init.sh

# Install Oh My Zsh
# See: https://ohmyz.sh
ARG OH_MY_ZSH_INSTALLATION_SCRIPT_URL="https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh"
RUN sh -c "$(wget ${OH_MY_ZSH_INSTALLATION_SCRIPT_URL} -O -)"

# Clean up apt cache
RUN apt-get clean && \
    rm -rf /var/lib/apt/lists/*
