# FROM python:3.9.23-alpine3.22 AS builder
# WORKDIR /build

# # Install build dependencies
# RUN apk add --no-cache python3-dev build-base linux-headers pcre-dev
# COPY requirements.txt .
# RUN pip3 install --no-cache-dir --prefix=/install -r requirements.txt

# FROM python:3.9.23-alpine3.22
# EXPOSE 8080
# WORKDIR /opt/server
# ENV CART_HOST="cart" \
#     CART_PORT="8080" \
#     USER_HOST="user" \
#     USER_PORT="8080" \
#     AMQP_HOST="rabbitmq" \
#     AMQP_USER="roboshop" \
#     AMQP_PASS="roboshop123"

# RUN apk add --no-cache pcre
# RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
# USER roboshop

# COPY --from=builder /install /usr/local
# COPY --chown=roboshop:roboshop payment.ini .
# COPY --chown=roboshop:roboshop *.py .

# CMD ["uwsgi", "--ini", "payment.ini"]


FROM python:3.9
ENV CART_HOST="cart" \
    CART_PORT="8080" \
    USER_HOST="user" \
    USER_PORT="8080" \
    AMQP_HOST="rabbitmq" \
    AMQP_USER="roboshop" \
    AMQP_PASS="roboshop123"
WORKDIR /opt/server/
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
COPY payment.ini .
COPY *.py .
COPY requirements.txt .
RUN pip3 install -r requirements.txt
RUN chown -R roboshop:roboshop /opt/server
USER roboshop

CMD ["uwsgi", "--ini", "payment.ini"]