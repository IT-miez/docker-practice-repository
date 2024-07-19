
FROM node:16-alpine

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

ENV REACT_APP_BACKEND_URL=http://127.0.0.1:8080/

RUN npm run build

RUN npm install -g serve

# Set the environment variable for the backend URL
# Uncomment the line below if you need to set the backend URL at build time
ENV REACT_APP_BACKEND_URL=http://127.0.0.1:8080/

EXPOSE 5000

CMD ["serve", "-s", "-l", "5000", "build"]
