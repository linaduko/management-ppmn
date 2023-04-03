FROM python:3.9.16-alpine

ENV PYTHONDONTWRITEBYTECODE = 1 \
     PYTHONUNBUFFERD = 1

RUN apk update && apk add --no_cache --no_cache_dir --virtual bash gcc musl-dev linux-headers jpeg-dev zlib-dev mariadb-dev libffi-dev

COPY requirements.txt /requirements.txt
RUN pip install --upgrade pip
RUN pip install -r requirements.txt
RUN rm /usr/bin/mysql*
COPY uwsgi.ini /uwsgi.ini

CMD ["uwsgi", "--ini", "/uwsgi.ini"]
