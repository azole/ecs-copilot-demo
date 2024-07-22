FROM node:22-alpine3.19

WORKDIR /app

COPY src/package.json /app

RUN npm install

COPY src /app

EXPOSE 3000

CMD ["npm", "start"]