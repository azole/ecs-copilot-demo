FROM node:22-alpine3.19 AS builder

ARG VITE_API_URL=http://localhost:3000
ENV VITE_API_URL=$VITE_API_URL
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

###################################
FROM nginx:alpine

WORKDIR /usr/share/nginx/html

EXPOSE 80

COPY --from=builder /app/dist .
