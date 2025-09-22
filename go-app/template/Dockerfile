# syntax=docker/dockerfile:1
FROM golang:1.24-alpine AS builder
WORKDIR /src

# 1) cache de dependências
COPY go.mod go.sum ./
RUN go mod download
# 2) copia o código e garante o go.sum (caso a dependência só esteja no source)
COPY . .
RUN go mod tidy

# 3) build
RUN --mount=type=cache,target=/root/.cache/go-build \
    CGO_ENABLED=0 GOOS=linux GOARCH=amd64 \
    go build -ldflags="-s -w" -o /out/app ./cmd/web

# runtime
FROM alpine:3.20
RUN apk add --no-cache ca-certificates tzdata
WORKDIR /app
COPY --from=builder /out/app /app/${{values.app_name}}
EXPOSE 3333
CMD ["/app/${{values.app_name}}"]
