# Build the simulator.
FROM golang:1-alpine AS builder
ARG GOPROXY
ENV GOPROXY=${GOPROXY}
RUN apk --no-cache add gcc musl-dev linux-headers
ADD . /genesis
WORKDIR /genesis
RUN go build .

# Build the runner container.
FROM alpine:latest
ADD . /
COPY --from=builder /genesis/genesis /
ENTRYPOINT ["./genesis"]
