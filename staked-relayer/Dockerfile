# ===== FIRST STAGE ======

FROM registry.gitlab.com/interlay/containers/rust-base:nightly-2021-01-25 as builder
ARG PROFILE=release
WORKDIR /app

COPY . /app

RUN cargo build "--$PROFILE" --package staked-relayer

# ===== SECOND STAGE ======

FROM bitnami/minideb:buster
ARG PROFILE=release

COPY --from=builder /app/target/$PROFILE/staked-relayer /usr/local/bin

# Checks
RUN ldd /usr/local/bin/staked-relayer && \
	/usr/local/bin/staked-relayer --version

CMD ["/usr/local/bin/staked-relayer"]
