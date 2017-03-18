FROM debian:stable-slim

LABEL \
    maintainer="Morgan Auchede <morgan.auchede@gmail.com>"

ENV \
    SSHUTTLE_VERSION=0.78.1

RUN set -x \

    # Prepare system

    && export DEBIAN_FRONTEND=noninteractive \

    && apt-get update \

    # Install packages

    && BUILD_DEPS="ca-certificates curl git" \

    && apt-get install -y --no-install-recommends \
           ${BUILD_DEPS} \
           iptables \
           python \
           python-setuptools \
           ssh-client \

    # Install sshuttle

    && git clone --branch "v${SSHUTTLE_VERSION}" "https://github.com/sshuttle/sshuttle.git" /tmp/sshuttle \
    && sh -c "cd /tmp/sshuttle && ./setup.py install" \

    # Install timonier/dumb-entrypoint

    && curl -sL "https://github.com/timonier/dumb-entrypoint/raw/master/bin/installer" | INSTALL_DIRECTORY="/usr/sbin" sh -s install \

    # Clean

    && apt-get remove -y --purge \
           ${BUILD_DEPS} \
    && apt-get autoremove -y --purge \

    && rm -rf \
           /tmp/* \
           /var/lib/apt/lists/*

ENTRYPOINT [ "dumb-init" , "--" , "dumb-entrypoint" , "sshuttle" ]
