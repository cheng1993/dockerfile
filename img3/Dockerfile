FROM nginx:1.14-alpine

ARG author="MageEdu <mage@magedu.com>"
LABEL maintainer="${author}"

ENV NGX_DOC_ROOT='/data/web/html/'

ADD index.html ${NGX_DOC_ROOT}
ADD entrypoint.sh /bin/

EXPOSE 80/tcp

HEALTHCHECK --start-period=3s CMD wget -O - -q http://${IP:-0.0.0.0}:10080/

ONBUILD ADD http://nginx.org/download/nginx-1.21.0.tar.gz /usr/local/src/

CMD ["/usr/sbin/nginx","-g","daemon off;"]

ENTRYPOINT ["/bin/entrypoint.sh"]
