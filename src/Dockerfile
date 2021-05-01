FROM node:16.0 AS overlaybuilder
ARG APP_BASEPATH
WORKDIR /build
COPY ./overlay/package.json .
RUN npm install

COPY ./overlay .
RUN npm run build

FROM node:16.0
WORKDIR /app
COPY ./server .

RUN npm install

COPY --from=overlaybuilder /build/dist ./overlay

CMD ["npm", "start"]