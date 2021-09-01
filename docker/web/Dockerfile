FROM golang:1.17-buster
RUN apt update && apt install git

RUN go install github.com/cosmtrek/air@v1.27.3
RUN go install github.com/99designs/gqlgen@v0.13.0

RUN mkdir /go/src/app
WORKDIR /go/src/app
ADD . /go/src/app
