FROM python:3-alpine

ARG BUILD_DEP='build-base libffi-dev openssl-dev'
ARG RUN_DEP='openssl ca-certificates'

ENV ANSIBLE_STRATEGY_PLUGINS=/usr/local/lib/python3.9/site-packages/ansible_mitogen/plugins/strategy \
    ANSIBLE_STRATEGY=mitogen_linear

RUN apk --update add ${BUILD_DEP} ${RUN_DEP} \
 && pip install -U pip \
 && pip install 'ansible<2.10' netaddr mitogen \
 && apk del ${BUILD_DEP} \
 && rm -rf /root/.cache \
 && rm -rf /var/cache/apk* \
 && mkdir -p /etc/ansible \
 && echo 'localhost ansible_connection=local' > /etc/ansible/hosts

ENTRYPOINT [ "ansible-playbook" ]
CMD ["--version"]
