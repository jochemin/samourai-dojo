FROM node:8

#################################################################
# INSTALL EXPLORER
#################################################################

ENV     EXPLORER_URL         https://github.com/janoside/btc-rpc-explorer/archive/v1.1.4.tar.gz
ENV     APP_DIR              /home/node/app

# Create app directory
RUN     mkdir "$APP_DIR" && \
        chown -R node:node "$APP_DIR"

RUN     set -ex && \
	wget -qO explorer.tar.gz "$EXPLORER_URL" && \
        tar -xzvf explorer.tar.gz --strip-components 1 && \
        rm explorer.tar.gz && \
        npm install

# Copy wait-for-it script
COPY    wait-for-it.sh "$APP_DIR/wait-for-it.sh"

RUN     chown node:node "$APP_DIR/wait-for-it.sh" && \
        chmod u+x "$APP_DIR/wait-for-it.sh" && \
        chmod g+x "$APP_DIR/wait-for-it.sh"

EXPOSE 3002

USER node
