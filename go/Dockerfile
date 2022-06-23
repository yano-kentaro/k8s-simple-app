FROM golang:1.18.1-bullseye as builder
RUN apt-get update \
    apt-get install -y --no-install-recommends \
    g++ \
    gcc \
    libc6-dev \
    make \
    pkg-config
WORKDIR /go/src/app
COPY ./app /go/src/app
RUN go build -o /output ./main.go

FROM alpine:3.16
COPY --from=builder /output .
ENTRYPOINT [ "./output" ]