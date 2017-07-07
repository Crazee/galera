FROM alpine:3.6

# Requirements
RUN apk update \
	&& apk add alpine-sdk

RUN apk add scons boost-dev

RUN apk add asio-dev check-dev \
	&& cp /usr/include/poll.h /usr/include/sys

COPY wordsize.h /usr/include/bits/

RUN adduser -h /out -u 1000 -D build \
	&& chgrp build /lib \
	&& chmod 775 /lib

COPY makeme /usr/bin

USER build
WORKDIR /src

ENTRYPOINT ["makeme"]
