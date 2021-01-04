FROM golang:1.15.6-buster

WORKDIR /app/
ENV GO111MODULE=auto
RUN apt-get update && apt-get -y install libprotobuf-dev protobuf-compiler

# Install grpc
RUN go get -u -v github.com/golang/protobuf/proto
RUN go get -u -v github.com/golang/protobuf/protoc-gen-go
RUN go get -u -v google.golang.org/grpc
RUN go get -u -v github.com/leonardyeoxl/go-grpc-server-streaming-example/src/proto

# Install protoc and zip system library
RUN apt-get update && apt-get install -y zip && \
    mkdir /opt/protoc && cd /opt/protoc && wget https://github.com/protocolbuffers/protobuf/releases/download/v3.7.0/protoc-3.7.0-linux-x86_64.zip && \
    unzip protoc-3.7.0-linux-x86_64.zip

ENV PATH=$PATH:$GOPATH/bin:/opt/protoc/bin

COPY start.sh .
RUN chmod +x start.sh