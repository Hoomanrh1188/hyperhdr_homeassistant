ARG BUILD_FROM=ghcr.io/hassio-addons/base:14.3.3
FROM $BUILD_FROM

# Install dependencies
RUN apk add --no-cache \
    cmake git build-base qt5-qtbase-dev libusb-dev ffmpeg-dev v4l-utils \
    && git clone https://github.com/awawa-dev/HyperHDR.git /src \
    && cd /src && mkdir build && cd build \
    && cmake .. -DCMAKE_BUILD_TYPE=Release \
    && make -j$(nproc) \
    && make install

# Copy run script
COPY run.sh /
RUN chmod +x /run.sh

CMD [ "/run.sh" ]
