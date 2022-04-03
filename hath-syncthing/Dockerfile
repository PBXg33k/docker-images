FROM frosty5689/hath:latest

EXPOSE 8384 22000/tcp 22000/udp 21027/udp
VOLUME ["/var/syncthing", "/hath/cache", "/hath/data", "/hath/download", "/hath/log", "/hath/tmp"]

RUN apk add --no-cache ca-certificates su-exec tzdata && apk upgrade -y

# Copy golang from golang image
COPY --from=golang:alpine /usr/local/go/ /usr/local/go/
# Copy syncthing from syncthing image
COPY --from=syncthing/syncthing:latest /bin/syncthing /bin/syncthing
COPY --from=syncthing/syncthing:latest /bin/entrypoint.sh /bin/entrypoint.sh

ENV PATH="/usr/local/go/bin:${PATH}"
ENV STGUIADDRESS=0.0.0.0:8384

CMD ["/opt/hath/start.sh"]