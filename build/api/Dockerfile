FROM node:lts-iron
LABEL authors="tinsuki"

USER root

ENV NODE_ENV=development

WORKDIR /app

RUN groupmod -g 1001 node && usermod -u 1001 -g 1001 node

ARG USER_NAME
ARG USER_ID
ARG GROUP_NAME
ARG GROUP_ID

RUN if [ ! -z ${USER_NAME} ] && [ ! -z ${GROUP_NAME} ] && [ ${USER_ID:-0} -ne 0 ] && [ ${GROUP_ID:-0} -ne 0 ] ; then \
    useradd -G www-data,root -u $USER_ID -d /home/$USER_NAME $USER_NAME && \
    mkdir -p /home/$USER_NAME/.composer  && \
    chown -Rf ${USER_NAME}:${GROUP_NAME} /home/$USER_NAME  && \
    chown -R ${USER_NAME}:${GROUP_NAME} /app \
    ; fi

USER ${USER_ID:-0}:${GROUP_ID:-0}
EXPOSE 3000