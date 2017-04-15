FROM python:latest

LABEL \
    maintainer="Morgan Auchede <morgan.auchede@gmail.com>"

ENV \
    SSHUTTLE_VERSION=latest

RUN set -eux \

    # Prepare system

    && export DEBIAN_FRONTEND=noninteractive \

    && apt-get update \

    # Install packages

    && export BUILD_DEPS="ca-certificates curl git" \

    && apt-get install --no-install-recommends --yes \
           ${BUILD_DEPS} \
           iptables \
           ssh-client \

    # Install dumb-entrypoint

    && curl --location "https://github.com/timonier/dumb-entrypoint/raw/master/bin/installer" | INSTALL_DIRECTORY="/usr/sbin" sh -s install \

    # Install sshuttle

    && export $(curl "https://raw.githubusercontent.com/timonier/version-lister/release/generated/sshuttle/${SSHUTTLE_VERSION}" | xargs) \

    && git clone --branch "v${SSHUTTLE_VERSION}" "https://github.com/sshuttle/sshuttle.git" /tmp/sshuttle \
    && sh -c "cd /tmp/sshuttle && ./setup.py install" \

    # Clean

    && apt-get remove --purge --yes \
           ${BUILD_DEPS} \
    && apt-get autoremove --purge --yes \

    && rm --force --recursive \
           /tmp/* \
           /var/lib/apt/lists/*

ENTRYPOINT [ "dumb-init" , "--" , "dumb-entrypoint" ]
