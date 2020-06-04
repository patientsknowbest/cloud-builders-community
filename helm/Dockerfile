FROM gcr.io/cloud-builders/gcloud

ARG HELM_VERSION=v3.2.0
ENV HELM_VERSION=$HELM_VERSION
ARG HELM_DIFF_VERSION=v3.1.1
ENV HELM_DIFF_VERSION=$HELM_DIFF_VERSION

COPY helm.bash /builder/helm.bash

RUN chmod +x /builder/helm.bash && \
  mkdir -p /builder/helm && \
  apt-get update && \
  apt-get install -y curl && \
  curl -SL https://get.helm.sh/helm-${HELM_VERSION}-linux-amd64.tar.gz -o helm.tar.gz && \
  tar zxvf helm.tar.gz --strip-components=1 -C /builder/helm linux-amd64 && \
  rm helm.tar.gz && \
  apt-get --purge -y autoremove && \
  apt-get clean && \
  rm -rf /var/lib/apt/lists/*

ENV PATH=/builder/helm/:$PATH

RUN helm plugin install https://github.com/databus23/helm-diff --version ${HELM_DIFF_VERSION}

