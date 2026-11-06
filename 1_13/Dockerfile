FROM ubuntu:24.04

WORKDIR /usr/src/app

RUN apt-get update && apt-get install -y gcc ca-certificates && update-ca-certificates

COPY go1.16.linux-amd64.tar.gz .

RUN tar -C /usr/local -xzf go1.16.linux-amd64.tar.gz && \
    rm go1.16.linux-amd64.tar.gz

ENV PATH="/usr/local/go/bin:${PATH}"
ENV PORT=8080
ENV REQUEST_ORIGIN=https://example.com

COPY . .

RUN go build

RUN go test ./...

CMD ["./server"]