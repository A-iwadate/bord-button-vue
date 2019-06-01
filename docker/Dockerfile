FROM node:10.16-alpine

ENV LANG C.UTF-8
ENV TZ Asia/Tokyo

RUN npm install -g yarn && \
    yarn global add @vue/cli && \
    yarn global add @vue/cli-init 

WORKDIR /app

CMD ["/bin/ash"]