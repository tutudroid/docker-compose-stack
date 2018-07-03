FROM kevin2333/my_ubuntu

COPY ./requirements.txt /tmp/

RUN pip install -r /tmp/requirements.txt

RUN mkdir -p /home/django/gailvlun

WORKDIR /home/django/gailvlun

ENV DJANGO_SETTINGS_MODULE='gailvlun.settings.production'
ENV C_FORCE_ROOT="true"

ENV TZ=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

EXPOSE 3031
EXPOSE 8888
EXPOSE 8011
EXPOSE 8080

RUN mkdir -p /etc/letsencrypt/live/api.gailvlun.site/

RUN mkdir -p /var/log/supervisor
COPY ./supervisord.conf /etc/supervisor/supervisord.conf

CMD ["supervisord", "-c", "/etc/supervisor/supervisord.conf"]


