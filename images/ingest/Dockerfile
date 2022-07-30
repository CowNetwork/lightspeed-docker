FROM rust:1-alpine3.16 AS builder
WORKDIR /build
COPY . .
RUN apk update \
    && apk add build-base \
    && cargo build --release

FROM alpine:3.16
COPY --from=builder /build/target/release/lightspeed-ingest /app/ingest
CMD ["/app/ingest"]
