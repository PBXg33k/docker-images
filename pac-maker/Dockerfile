FROM python:3-alpine

RUN apk add --update git \
	&& git clone https://github.com/lintmx/pac-maker.git --depth=1 --no-tags \
	&& rm -rf /pac-maker/.git \
	&& apk del git \
	&& rm -rf /var/cache/apk

WORKDIR /pac-maker

ENTRYPOINT ["/pac-maker/make.py"]
