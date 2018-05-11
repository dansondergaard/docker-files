FROM alpine:latest AS builder
WORKDIR /root
RUN apk add --update wget unzip alpine-sdk
RUN wget http://users-birc.au.dk/cstorm/software/rapidnj/rapidnj-src-2.3.2.zip && \
    unzip rapidnj-src-2.3.2.zip && \
    cd rapidNJ/ && \
    make

FROM alpine:latest
RUN apk add --update libstdc++ libgcc
WORKDIR /root
COPY --from=builder /root/rapidNJ/bin/rapidnj /usr/bin/
