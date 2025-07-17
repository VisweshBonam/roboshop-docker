FROM nginx
EXPOSE 80
RUN rm -rf /usr/share/nginx/html/index.html
RUN rm -rf /etc/nginx/nginx.conf

COPY src/ /usr/share/nginx/html/
COPY nginx.conf /etc/nginx/nginx.conf

ENV CATALOGUE_HOST="catalogue" \
    CATALOGUE_PORT="8080" \
    CART_HOST="cart" \
    CART_PORT="8080" \
    USER_HOST="user" \
    USER_PORT="8080" \
    SHIPPING_HOST="shipping" \
    SHIPPING_PORT="8080" \
    PAYMENT_HOST="payment" \
    PAYMENT_PORT="8080"