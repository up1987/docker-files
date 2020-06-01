FROM python:3-alpine

ARG BUILD_DEP='build-base libffi-dev openssl-dev'
ARG RUN_DEP='openssl ca-certificates'

RUN apk --update add ${BUILD_DEP} ${RUN_DEP} \
 && pip install -U pip \
 && pip install 'ansible<2.8' \
 && apk del ${BUILD_DEP} \
 && rm -rf /root/.cache \
 && rm -rf /var/cache/apk*

ENTRYPOINT [ "ansible-playbook", "--version" ]
