FROM node:16

RUN npm install -g @vue/cli

ARG UID
ARG USER_NAME

RUN usermod -u 1001 node && \
    useradd -m -u ${UID} -g root ${USER_NAME}