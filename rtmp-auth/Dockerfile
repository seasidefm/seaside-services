FROM golang:1.21.7-bookworm as builder

RUN apt-get update -y
RUN apt-get install -y protobuf-compiler git

RUN go install github.com/rakyll/statik@latest
RUN go install google.golang.org/protobuf/cmd/protoc-gen-go@v1.28
RUN go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@v1.2

WORKDIR /build-dir
RUN git clone https://github.com/seasidefm/rtmp-auth.git .

RUN make

FROM alpine

WORKDIR /app
COPY --from=builder /build-dir/rtmp-auth ./

CMD [ "./rtmp-auth" ]
