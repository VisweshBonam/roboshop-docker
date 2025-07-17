FROM nginx
RUN rm -rf /usr/share/nginx/html/index.html
RUN rm -rf /etc/nginx/nginx.conf

COPY src/ /usr/share/nginx/html/
COPY nginx.conf /etc/nginx/nginx.conf

ENV CART_HOST="cart" \
    USER_HOST="user" \
    CATALOGUE_HOST="catalogue" \
    SHIPPING_HOST="shipping" \
    PAYMENT_HOST="payment"
