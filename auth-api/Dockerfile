FROM golang:1.18-alpine AS builder

WORKDIR /app
COPY go.* ./
RUN go mod download

COPY . .
RUN go build -o auth-service .

FROM alpine:3.15
WORKDIR /app
COPY --from=builder /app/auth-service .

EXPOSE 8000
CMD ["./auth-service"]