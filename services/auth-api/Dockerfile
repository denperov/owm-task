FROM golang:1.10-alpine as builder
WORKDIR /go/src/github.com/denperov/owm-task
COPY . .
RUN CGO_ENABLED=0 go test ./...
RUN CGO_ENABLED=0 go build -o /out/auth-api ./services/auth-api

FROM scratch
EXPOSE  8080
WORKDIR /app
COPY --from=builder /out/auth-api ./
CMD ["./auth-api"]