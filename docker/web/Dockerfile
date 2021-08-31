FROM golang:1.17-buster
RUN apt update && apt install git

RUN go install github.com/cosmtrek/air@v1.27.3

RUN mkdir /go/src/go-gqlgen-template
WORKDIR /go/src/go-gqlgen-template
ADD . /go/src/go-gqlgen-template
