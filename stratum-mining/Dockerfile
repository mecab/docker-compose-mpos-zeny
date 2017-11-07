FROM alpine:3.6

MAINTAINER mecab <mecab@misosi.ru>

WORKDIR /work

RUN apk update && \
    apk add alpine-sdk git curl python python-dev

RUN git clone https://github.com/ahmedbodi/stratum-mining.git && \
    git clone https://github.com/ahmedbodi/stratum.git && \
    git clone https://github.com/bitzeny/zny_yescrypt_python.git

RUN cd stratum-mining && \
    git submodule init && \
    git submodule update && \
    curl https://gist.githubusercontent.com/bitzeny/9db1723161bc2650a1b1/raw/82197337372d4cd2079cd21c948bc6151fa1ca62/stratum.patch | tail +4  > stratum.patch && \
    patch -p1 < stratum.patch

RUN apk add py-pip

RUN cd stratum && \
    sed -i -e "s/http/https/" distribute_setup.py && \
    sed -i -e "s/0.6.28/0.7.3/" distribute_setup.py && \
    python setup.py install

RUN cd zny_yescrypt_python && python setup.py install
