FROM node:12.18.2-alpine3.12

ARG USER_NAME
ARG GROUP_NAME
ARG USER_UID
ARG USER_GID
ARG WORK_DIR

RUN deluser --remove-home node \
    && addgroup -g $USER_GID -S $GROUP_NAME \
    && adduser -u $USER_UID -s /bin/sh -S $USER_NAME $GROUP_NAME

RUN apk --update --no-cache add git curl bash openssh-client sudo jq

RUN echo "$USER_NAME ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers.d/${USER_NAME} \
    && chmod 0440 /etc/sudoers.d/$USER_NAME

USER vscode
RUN mkdir /home/${USER_NAME}/${WORK_DIR}
WORKDIR /home/${USER_NAME}/${WORK_DIR}