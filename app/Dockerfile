FROM node:12-alpine
ENV APPDIR /app
RUN mkdir -p ${APPDIR}
WORKDIR ${APPDIR}
RUN apk add --update --no-cache zlib-dev libpng-dev
COPY package.json ${APPDIR}
COPY yarn.lock ${APPDIR}

RUN  apk add --update --no-cache --virtual .build-deps make bash g++ && \
     yarn install && \
     apk del .build-deps
COPY public/ ${APPDIR}/public/
COPY server.js ${APPDIR}/
EXPOSE 8080
CMD ["node", "server.js"]