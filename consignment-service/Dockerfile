FROM golang:alpine as builder

RUN apk update && apk upgrade && \
    apk add --no-cache git gcc musl-dev

RUN mkdir /app
WORKDIR /app

ENV GO111MODULE=on

COPY . .

ENV CGO_ENABLED=0

RUN go mod download
RUN CG0_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o shippy-service-consignment

# Run container
FROM alpine:latest

RUN apk --no-cache add ca-certificates

RUN mkdir /app
WORKDIR /app
COPY --from=builder /app/shippy-service-consignment .

CMD ["./shippy-service-consignment"]
