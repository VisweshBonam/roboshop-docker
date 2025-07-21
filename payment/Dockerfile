FROM python:3.9.23-alpine3.22 AS builder
WORKDIR /opt/server
COPY payment.ini .
COPY *.py .
COPY requirements.txt .
RUN apk add --no-cache --virtual .build-deps \
        gcc musl-dev python3-dev libffi-dev linux-headers && \
    pip3 install --no-cache-dir -r requirements.txt && \
    apk del .build-deps

FROM python:3.9.23-alpine3.22
ENV CART_HOST="cart" \
    CART_PORT="8080" \
    USER_HOST="user" \
    USER_PORT="8080" \
    AMQP_HOST="rabbitmq" \
    AMQP_USER="roboshop" \
    AMQP_PASS="roboshop123"

WORKDIR /opt/server
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
RUN chown -R roboshop:roboshop /opt/server
RUN apk add --no-cache libstdc++ libffi
COPY --from=builder /opt/server /opt/server
USER roboshop
CMD ["uwsgi", "--ini", "payment.ini"]

# FROM python:3.9
# WORKDIR /opt/server/
# COPY payment.ini .
# COPY *.py .
# COPY requirements.txt .
# RUN pip3 install -r requirements.txt
# ENV CART_HOST="cart" \
#     CART_PORT="8080" \
#     USER_HOST="user" \
#     USER_PORT="8080" \
#     AMQP_HOST="rabbitmq" \
#     AMQP_USER="roboshop" \
#     AMQP_PASS="roboshop123"

# CMD ["uwsgi", "--ini", "payment.ini"]