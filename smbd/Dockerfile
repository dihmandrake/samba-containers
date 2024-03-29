FROM ubuntu:23.10

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

# The healtcheck is fairly expensive; Do not execute oftens
HEALTHCHECK --interval=300s --timeout=30s --start-period=5s --retries=3 CMD [ "/usr/bin/smbstatus", "--fast", "--numeric", "--brief" ]
EXPOSE 445/tcp

ENTRYPOINT ["/usr/sbin/smbd", "--foreground", "--no-process-group", "--debug-stdout"]
CMD []
