FROM alpine:latest AS builder

WORKDIR /root
RUN apk add --update wget cmake alpine-sdk
RUN wget http://users-cs.au.dk/cstorm/software/tqdist/files/tqDist-1.0.1.tar.gz && \
    tar xf tqDist-1.0.1.tar.gz && \
    cd tqDist-1.0.1/ && \
    cmake . && \
    make

FROM alpine:latest
RUN apk add --update libstdc++ libgcc
COPY --from=builder /root/tqDist-1.0.1/bin/triplet_dist \
                    /root/tqDist-1.0.1/bin/quartet_dist \
                    /root/tqDist-1.0.1/bin/pairs_triplet_dist \
                    /root/tqDist-1.0.1/bin/pairs_quartet_dist \
                    /root/tqDist-1.0.1/bin/all_pairs_triplet_dist \
                    /root/tqDist-1.0.1/bin/all_pairs_quartet_dist /usr/bin/
WORKDIR /root
