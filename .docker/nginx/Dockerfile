FROM nginx:1.22.0

RUN apt-get update -qq && apt-get -y install apache2-utils

ENV RAILS_ROOT /app

WORKDIR $RAILS_ROOT
COPY ./rails/public public/
COPY ./.docker/nginx/nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80

CMD [ "nginx", "-g", "daemon off;" ]
