FROM alpine
ARG PJS_VER=2.1.1
ADD repositories /etc/apk/repositories
RUN apk update
RUN apk add fontconfig ca-certificates bzip2 curl font-ipa
RUN apk add python3-dev py3-pip py3-lxml py3-zmq py3-yaml py3-pillow py3-requests py3-click py3-decorator py3-idna py3-jedi py3-jinja2 py3-jsonschema py3-markupsafe py3-olefile py3-pexpect py3-pygments py3-dateutil py3-six py3-toml py3-tornado py3-urllib3 py3-wcwidth
RUN pip3 install jupyter
RUN pip3 install selenible
RUN fc-cache
RUN jupyter kernelspec install /usr/lib/python3.6/site-packages/selenible/seleniblepiter
RUN curl -L https://github.com/dustinblackman/phantomized/releases/download/2.1.1/dockerized-phantomjs.tar.gz | tar xz -C /
RUN curl -L https://bitbucket.org/ariya/phantomjs/downloads/phantomjs-${PJS_VER}-linux-x86_64.tar.bz2 | \
    tar xj -C /tmp phantomjs-${PJS_VER}-linux-x86_64/bin/phantomjs && \
    mv /tmp/phantomjs-${PJS_VER}-linux-x86_64/bin/phantomjs /usr/local/bin/ && \
    rm -r /tmp/phantomjs-${PJS_VER}-linux-x86_64
RUN adduser jupyter -D
EXPOSE 8888
USER jupyter
CMD ["jupyter", "notebook", "--ip=0.0.0.0", "--port=8888"]
