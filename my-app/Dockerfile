# Build Stage
FROM golang:1.21-bookworm AS build

WORKDIR /app
COPY go.mod go.sum ./
RUN go mod download && go mod verify

COPY main.go ./
RUN go build -o /my-app

# Use debian-slim instead of distroless
FROM debian:bookworm-slim

COPY --from=build /my-app /my-app

RUN apt-get update && apt-get install -y libc6

ENTRYPOINT ["/my-app"]
