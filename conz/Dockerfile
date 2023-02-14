FROM golang:1.20.0-alpine3.17 AS build

WORKDIR /app

COPY go.mod ./

COPY go.sum ./

RUN go mod download

COPY *.go ./

RUN go build -o conz

FROM alpine:3.15

WORKDIR /

COPY --from=build /app/conz /conz

EXPOSE 8080

ENTRYPOINT ["/conz"]
