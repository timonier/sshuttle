FROM python:slim

LABEL \
    maintainer="Morgan AUCHEDE <morgan.auchede@gmail.com>"

ENV \
    LC_ALL=C.UTF-8

RUN set -e -u -x \
\
    # Prepare system
\
    && export DEBIAN_FRONTEND=noninteractive \
    && apt-get update \
\
    # Install packages
\
    && BUILD_DEPS="curl git" \
    && apt-get install --no-install-recommends --yes ${BUILD_DEPS} ca-certificates iptables locales ssh-client \
\
    # Install sshuttle
\
    && pip install sshuttle \
\
    # Clean
\
    && apt-get remove --purge --yes ${BUILD_DEPS} \
    && apt-get autoremove --purge --yes \
    && rm -f -r /root/.cache /tmp/* /var/lib/apt/lists/*
