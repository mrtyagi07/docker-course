FROM node:20-alpine
USER app
WORKDIR /app
COPY package*.json ./
USER root
RUN npm install
COPY . .
EXPOSE 8000
CMD npm start