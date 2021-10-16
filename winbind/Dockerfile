FROM ubuntu:20.04

# hadolint ignore=DL3008
RUN set -eux \
    && apt-get update \
    && apt-get install -y --no-install-recommends \
        winbind \
    && apt-get clean \
    && apt-get clean autoclean \
    && apt-get autoremove --yes \
    && rm -rf /var/lib/apt/lists/*

ENTRYPOINT ["/usr/sbin/winbindd", "--foreground", "--no-process-group", "--stdout"]
CMD []
