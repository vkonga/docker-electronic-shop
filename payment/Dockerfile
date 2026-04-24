FROM python:3.9.23-alpine3.22
EXPOSE 8080
WORKDIR /opt/server
COPY requirements.txt .
COPY payment.ini .
COPY *.py .
RUN addgroup -S electronic-shop && adduser -S electronic-shop -G electronic-shop \
    && chown -R electronic-shop:electronic-shop /opt/server

RUN pip3 install -r requirements.txt
CMD ["uwsgi", '--ini',"payment.ini"]