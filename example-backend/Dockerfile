
FROM golang:1.16-alpine


WORKDIR /app

COPY go.mod go.sum ./

RUN go mod download

# Install Redis
RUN apk add redis

RUN go get -u github.com/rs/cors

ENV PORT=8080
ENV REQUEST_ORIGIN=http://127.0.0.1:5000

COPY . .

RUN go build -o server .

EXPOSE 8080
ENV REDIS_HOST=localhost
#ENV POSTGRES_HOST=
#ENV POSTGRES_USER=postgres
#ENV POSTGRES_PASSWORD=postgres
#ENV POSTGRES_DATABASE=postgres

# Start server only
#CMD ./server

# Start Redis server and the Go server
CMD redis-server --daemonize yes && ./server
