FROM nginx:stable

ARG CERTBOT_EMAIL
ARG DOMAIN_NAME

COPY nginx.conf /etc/nginx/
COPY default.conf /etc/nginx/conf.d/

RUN  sed -i "s/{DOMAIN_NAME}/${DOMAIN_NAME}/g" /etc/nginx/conf.d/default.conf \
    && apt-get update && apt-get install -y apt-utils && apt-get install -y cron certbot python-certbot-nginx bash wget \
    && certbot certonly --standalone --agree-tos -m "${CERTBOT_EMAIL}" -n -d ${DOMAIN_NAME} \
    && rm -rf /var/lib/apt/lists/* \
    && echo "@weekly certbot renew --nginx > /dev/null 2>&1" >/etc/cron.d/certbot-renew \
    && crontab /etc/cron.d/certbot-renew

VOLUME /etc/letsencrypt

CMD [ "sh", "-c", "cron && nginx -g 'daemon off;'" ]
