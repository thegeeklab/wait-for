FROM alpine:3.12

LABEL maintainer="Robert Kaussow <mail@thegeeklab.de>" \
    org.label-schema.name="wait-for" \
    org.label-schema.vcs-url="https://github.com/thegeeklab/wait-for" \
    org.label-schema.vendor="Robert Kaussow" \
    org.label-schema.schema-version="1.0"

ADD wait-for /usr/local/bin/wait-for

USER root
CMD []
ENTRYPOINT ["/usr/local/bin/wait-for"]
