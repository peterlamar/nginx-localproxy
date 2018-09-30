FROM golang:1.11

WORKDIR /go/src/app
COPY exampleHandler.go .

RUN go get -d -v ./...
RUN go install -v ./...

WORKDIR /tmp

ENTRYPOINT ["app"]
