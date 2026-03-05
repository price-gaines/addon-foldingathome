ARG BUILD_FROM=ghcr.io/hassio-addons/debian-base:7.8.3
# hadolint ignore=DL3006
FROM ${BUILD_FROM}

# Set shell
SHELL ["/bin/bash", "-o", "pipefail", "-c"]

# Setup base system
ARG BUILD_ARCH=amd64
ARG FAH_CLIENT_SHA256="4f9c8bed9b2893752afb87e2796512ca0ca300ffc3d6035c518d56360370886c"
RUN \
    apt-get update \
    && apt-get install -y --no-install-recommends \
        ca-certificates \
        curl \
        bzip2 \
        ocl-icd-libopencl1 \
        coreutils \
    \
    && curl -fSL -o /tmp/fah.deb \
        "https://download.foldingathome.org/releases/public/fah-client/debian-10-64bit/release/fah-client_8.5.5_amd64.deb" \
    && echo "${FAH_CLIENT_SHA256}  /tmp/fah.deb" | sha256sum -c - \
    \
    && addgroup --system render \
    && mkdir -p /etc/fahclient \
    && touch /etc/fahclient/config.xml \
    && apt-get install -y --no-install-recommends /tmp/fah.deb \
    && dpkg -s fah-client | grep -q "^Version: 8.5.5" \
    && ln -sf /usr/bin/fah-client /usr/bin/FAHClient \
    \
    && rm -fr \
        /tmp/* \
        /var/{cache,log}/* \
        /var/lib/apt/lists/*

# Copy root filesystem
COPY rootfs /

# Build arguments
ARG BUILD_DATE
ARG BUILD_REF
ARG BUILD_VERSION
ARG BUILD_NAME="Folding@home"
ARG BUILD_DESCRIPTION="Fighting disease with a world wide distributed super computer"
ARG BUILD_REPOSITORY="hassio-addons/addon-foldingathome"

# Labels
LABEL \
    io.hass.name="${BUILD_NAME}" \
    io.hass.description="${BUILD_DESCRIPTION}" \
    io.hass.arch="${BUILD_ARCH}" \
    io.hass.type="addon" \
    io.hass.version="${BUILD_VERSION}" \
    maintainer="Franck Nijhof <frenck@addons.community>" \
    org.opencontainers.image.title="${BUILD_NAME}" \
    org.opencontainers.image.description="${BUILD_DESCRIPTION}" \
    org.opencontainers.image.vendor="Home Assistant Community Add-ons" \
    org.opencontainers.image.authors="Franck Nijhof <frenck@addons.community>" \
    org.opencontainers.image.licenses="MIT" \
    org.opencontainers.image.url="https://addons.community" \
    org.opencontainers.image.source="https://github.com/${BUILD_REPOSITORY}" \
    org.opencontainers.image.documentation="https://github.com/${BUILD_REPOSITORY}/blob/main/README.md" \
    org.opencontainers.image.created="${BUILD_DATE}" \
    org.opencontainers.image.revision="${BUILD_REF}" \
    org.opencontainers.image.version="${BUILD_VERSION}"
