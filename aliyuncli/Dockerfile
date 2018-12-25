FROM golang:alpine as builder

RUN apk add --update curl make git && \
    curl -o /usr/local/bin/jq -L https://github.com/stedolan/jq/releases/download/jq-1.6/jq-linux64 && \
	chmod +x /usr/local/bin/jq && \
    mkdir -p /go/src/github.com/aliyun/ && \
    curl -L https://github.com/aliyun/aliyun-cli/archive/v3.0.6.tar.gz \
    | tar -zxC /go/src/github.com/aliyun/ && \
    mv /go/src/github.com/aliyun/aliyun-cli-3.0.6 /go/src/github.com/aliyun/aliyun-cli && \
    cd  /go/src/github.com/aliyun/aliyun-cli && \
    make deps && make testdeps && make build

FROM alpine:3.8
COPY --from=builder /usr/local/bin/jq /usr/local/bin/jq
COPY --from=builder /go/src/github.com/aliyun/aliyun-cli/out/aliyun /usr/local/bin/aliyun
CMD ["aliyun"]
