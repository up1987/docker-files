FROM python

ARG PYPI_REPO='https://pypi.org/simple'

RUN pip install -i ${PYPI_REPO} 'ansible<2.8' \
 && rm -rf /root/.cache
