FROM alpine:3.11

ARG VCS_REF
ARG BUILD_DATE

# Metadata
LABEL org.label-schema.vcs-ref=$VCS_REF \
      org.label-schema.name="helm-kubectl" \
      org.label-schema.url="https://hub.docker.com/r/jmatiastw/helm-kubectl/" \
      org.label-schema.vcs-url="https://github.com/jmatias/docker-images" \
      org.label-schema.build-date=$BUILD_DATE

# Note: Latest version of kubectl may be found at:
# https://github.com/kubernetes/kubernetes/releases
ENV KUBE_LATEST_VERSION="v1.16.8"
# Note: Latest version of helm may be found at
# https://github.com/kubernetes/helm/releases
ENV HELM_VERSION="v3.2.2"

RUN apk add --no-cache ca-certificates bash git openssh curl
RUN wget -q https://storage.googleapis.com/kubernetes-release/release/${KUBE_LATEST_VERSION}/bin/linux/amd64/kubectl -O /usr/local/bin/kubectl
RUN chmod +x /usr/local/bin/kubectl
RUN wget -q https://get.helm.sh/helm-${HELM_VERSION}-linux-amd64.tar.gz -O - | tar -xzO linux-amd64/helm > /usr/local/bin/helm
RUN chmod +x /usr/local/bin/helm


WORKDIR /config

RUN helm repo add fluxcd https://charts.fluxcd.io
RUN helm repo add external-secrets https://godaddy.github.io/kubernetes-external-secrets/

CMD bash