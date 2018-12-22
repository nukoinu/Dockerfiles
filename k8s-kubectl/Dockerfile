FROM alpine:3.8

ENV KUBECTL_VERSION="v1.13.1"

RUN apk -v --update add \
     ca-certificates \
     python3 \
     groff \
     less \
     mailcap \
     curl \
     bash \
     bash-doc \
     bash-completion
RUN  curl -L https://storage.googleapis.com/kubernetes-release/release/${KUBECTL_VERSION}/bin/linux/amd64/kubectl -o /usr/local/bin/kubectl && \
     chmod +x /usr/local/bin/kubectl
RUN  python3 -m ensurepip && \
     rm -r /usr/lib/python*/ensurepip && \
     pip3 install --upgrade pip setuptools && \
     pip3 install --upgrade awscli==1.16.68 s3cmd==2.0.2 python-magic && \
     if [ ! -e /usr/bin/pip ]; then ln -s pip3 /usr/bin/pip ; fi && \
     if [[ ! -e /usr/bin/python ]]; then ln -sf /usr/bin/python3 /usr/bin/python; fi
RUN  rm /var/cache/apk/*

VOLUME /root/.aws
VOLUME /work
WORKDIR /work
