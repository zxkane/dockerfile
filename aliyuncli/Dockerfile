FROM alpine:3.8 AS builder

RUN apk add curl && \
    curl -o /usr/local/bin/jq -L https://github.com/stedolan/jq/releases/download/jq-1.6/jq-linux64 && \
	chmod +x /usr/local/bin/jq && \
    curl -L https://github.com/aliyun/aliyun-cli/releases/download/v3.0.6/aliyun-cli-linux-amd64.tar.gz \
    | tar -zxC /usr/local/bin

FROM alpine:3.8
RUN apk add --update ca-certificates && \
    update-ca-certificates
COPY --from=builder /usr/local/bin/jq /usr/local/bin/jq
COPY --from=builder /usr/local/bin/aliyun /usr/local/bin/aliyun
