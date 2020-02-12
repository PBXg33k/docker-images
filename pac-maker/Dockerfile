FROM python:3-alpine

RUN apk add --update git \
	&& git clone https://github.com/lintmx/pac-maker.git --depth=1 --no-tags \
	&& rm -rf /pac-maker/.git \
	&& apk del git \
	&& rm -rf /var/cache/apk \
	&& cd /pac-maker \
	&& wget https://github.com/stedolan/jq/releases/download/jq-1.6/jq-linux64 \
	&& mv jq-linux64 jq && chmod +x jq \
	&& cat data.json.example | ./jq 'del(.white_list[]) | del(.black_list) | del(.special_list)' > data.json \
	&& mv config.json.example config.json \
	&& rm jq


WORKDIR /pac-maker

ENTRYPOINT ["/pac-maker/make.py"]
