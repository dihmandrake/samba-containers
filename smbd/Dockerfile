FROM ubuntu:20.04

# hadolint ignore=DL3008
RUN set -eux \
    && apt-get update \
    && apt-get install -y --no-install-recommends \
        samba \
        # libnss-winbind Required for group resolution in Samba
        libnss-winbind \
        # For the vfs modules in config
        samba-vfs-modules \
    && apt-get clean \
    && apt-get clean autoclean \
    && apt-get autoremove --yes \
    && rm -rf /var/lib/apt/lists/* \
    && sed -i 's/^\(passwd:  *files\)/\1 winbind/' /etc/nsswitch.conf \
    && sed -i 's/^\(group:  *files\)/\1 winbind/' /etc/nsswitch.conf

ENTRYPOINT ["/usr/sbin/smbd", "--foreground", "--no-process-group", "--log-stdout"]
CMD []
