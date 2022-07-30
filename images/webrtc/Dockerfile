FROM golang:1.18 AS builder
WORKDIR /build
COPY . .
RUN GOOS=linux GOARCH=amd64 go build

FROM alpine:3.16
COPY --from=builder /build/lightspeed-webrtc /app/webrtc
RUN apk update && apk add libc6-compat
CMD ["/app/webrtc", "--addr=0.0.0.0"]

