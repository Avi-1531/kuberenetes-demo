FROM golang:1.21

WORKDIR /go/src/app

COPY *.go .

RUN go mod init dispatch && go get

# go mod init dispatch:
#     Initializes a Go module named dispatch in this directory.
#     Creates go.mod.
#     go get:
#     Pulls all dependencies referenced in your *.go files and writes them into go.mod / go.sum.

RUN go install
# Compiles the Go package in the current directory and installs the binary into $GOPATH/bin (in this image, usually /go/bin).
# Because your module is named dispatch, the resulting binary is named dispatch.
CMD dispatch
