FROM alpine:3.8 AS build
MAINTAINER zxkane@github

WORKDIR /root
ADD https://gosspublic.alicdn.com/fun/fun-v2.7.1-linux-x64.zip .
RUN unzip fun-v2.7.1-linux-x64.zip

FROM debian:8-slim
COPY --from=build /root/fun-v2.7.1-linux-x64 /usr/bin/fun