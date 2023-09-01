FROM alpine
LABEL maintainer="Fatih Boy <fatih.boy@enterprisecoding.com>"

RUN apk update \
  && apk add openldap-clients

ENTRYPOINT ["ldapsearch"]