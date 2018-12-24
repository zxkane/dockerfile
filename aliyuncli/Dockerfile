FROM alpine:3.8 AS builder

RUN apk add curl && \
    curl -o /usr/local/bin/jq -L https://github.com/stedolan/jq/releases/download/jq-1.6/jq-linux64 && \
	chmod +x /usr/local/bin/jq

FROM ellerbrock/alpine-aliyuncli
COPY --from=builder /usr/local/bin/jq /usr/local/bin/jq
