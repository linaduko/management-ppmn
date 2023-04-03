FROM python:3.9.16-alpine

ENV PYTHONDONTWRITEBYTECODE = 1 \
     PYTHONUNBUFFERD = 1

RUN apk update \
    && apk upgrade \
    && apk add --no-cache bash \
    && apk add --no-cache gcc \
    && apk add --no-cache musl-dev \ 
    && apk add --no-cache linux-headers \
    && apk add --no-cache jpeg-dev \
    && apk add --no-cache zlib-dev \
    && apk add --no-cache mariadb-dev \
    && apk add --no-cache libffi-dev

COPY requirements.txt /requirements.txt
RUN pip install --upgrade pip
RUN pip install -r requirements.txt
RUN rm /usr/bin/mysql*
COPY uwsgi.ini /uwsgi.ini

CMD ["uwsgi", "--ini", "/uwsgi.ini"]
