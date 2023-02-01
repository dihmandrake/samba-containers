FROM ubuntu:23.04

# hadolint ignore=DL3008
RUN set -eux \
    && apt-get update \
    && apt-get install -y --no-install-recommends \
        samba-common-bin \
        tdb-tools \
        adcli \
    && apt-get clean \
    && apt-get clean autoclean \
    && apt-get autoremove --yes \
    && rm -rf /var/lib/apt/lists/*

ENTRYPOINT ["/bin/bash"]
CMD []
