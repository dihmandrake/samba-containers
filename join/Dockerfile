FROM ubuntu:20.04

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
