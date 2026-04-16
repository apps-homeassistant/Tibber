ARG BUILD_FROM=ghcr.io/home-assistant/amd64-base:3.19
FROM $BUILD_FROM

ARG BUILD_ARCH

RUN apk add --no-cache libgcc mosquitto-clients jq curl

COPY backend/target/release/tibber_backend-* /tmp/
RUN case "${BUILD_ARCH}" in \
        amd64|aarch64) ;; \
        *) echo "Unsupported BUILD_ARCH: ${BUILD_ARCH}" && exit 1 ;; \
    esac && \
    mv "/tmp/tibber_backend-${BUILD_ARCH}" /usr/local/bin/tibber_backend && \
    rm -f /tmp/tibber_backend-* && \
    chmod +x /usr/local/bin/tibber_backend

COPY frontend/ /app/frontend/
COPY rootfs/ /

RUN mkdir -p /app/lib /app/.cache /app/.backup/keys /app/.temp

RUN chmod +x /etc/s6-overlay/s6-rc.d/tibber/run

WORKDIR /app
EXPOSE 8100
