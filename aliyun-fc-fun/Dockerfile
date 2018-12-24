FROM alpine:3.8 AS build
MAINTAINER zxkane@github

WORKDIR /root
ADD https://gosspublic.alicdn.com/fun/fun-v2.7.2-linux-x64.zip .
RUN apk add curl && \
    unzip fun-v2.7.2-linux-x64.zip && \
    curl -L "https://github.com/gliderlabs/sigil/releases/download/v0.4.0/sigil_0.4.0_$(uname -sm|tr \  _).tgz" \
    | tar -zxC .

FROM debian:8-slim
COPY --from=build /root/fun-v2.7.2-linux-x64 /usr/bin/fun
COPY --from=build /root/sigil /usr/bin/sigil