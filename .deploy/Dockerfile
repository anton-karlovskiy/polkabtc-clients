FROM ubuntu:20.10

ARG PROFILE=release
ARG BINARY=btc-parachain

COPY target/${PROFILE}/${BINARY} /usr/local/bin

# Checks
RUN chmod +x /usr/local/bin/${BINARY} && \
    ldd /usr/local/bin/${BINARY} && \
    /usr/local/bin/${BINARY} --version

CMD ["/usr/local/bin/${BINARY}"]
