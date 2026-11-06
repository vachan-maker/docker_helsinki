FROM golang:1.16

WORKDIR /usr/src/app

RUN apt-get update && \
    apt-get install -y gcc ca-certificates && \
    update-ca-certificates && \
    rm -rf /var/lib/apt/lists/*

ENV PORT=8080
ENV REQUEST_ORIGIN=https://example.com

COPY . .

RUN go build -o server

RUN go test ./...

CMD ["./server"]