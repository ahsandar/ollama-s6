ARG OLLAMA_VER=0.6.5
FROM docker.io/ollama/ollama:${OLLAMA_VER}

RUN apt-get -qq update && \
  apt-get -qq install -y xz-utils \
  && rm -rf /var/libs/apt/lists/*


ARG S6_OVERLAY_VERSION="3.2.0.0"
# Download the s6-overlay for process supervision.
ADD https://github.com/just-containers/s6-overlay/releases/download/v${S6_OVERLAY_VERSION}/s6-overlay-noarch.tar.xz /tmp
RUN tar -C / -Jxpf /tmp/s6-overlay-noarch.tar.xz
ADD https://github.com/just-containers/s6-overlay/releases/download/v${S6_OVERLAY_VERSION}/s6-overlay-x86_64.tar.xz /tmp
RUN tar -C / -Jxpf /tmp/s6-overlay-x86_64.tar.xz

# Copy s6 init & service definitions.
COPY etc/s6-overlay /etc/s6-overlay

# The kill grace time is set to zero because our app handles shutdown through SIGTERM.
ENV S6_KILL_GRACETIME=0

# Sync disks is enabled so that data is properly flushed.
ENV S6_SYNC_DISKS=1

# https://github.com/just-containers/s6-overlay/issues/577
ENV  S6_CMD_WAIT_FOR_SERVICES_MAXTIME=0

# Run the s6 init process on entry.
ENTRYPOINT [ "/init" ]

# CMD []


