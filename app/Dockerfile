FROM arm64v8/golang:1.12-alpine as builder
RUN apk update
WORKDIR /go/src/app
COPY . .

RUN CGO_ENABLED=0 GOOS=linux GOARCH=arm GOARM=6 go build -o app .

# Exec Container
FROM armhf/alpine:latest
COPY --from=builder /go/src/app/app ./
EXPOSE 8080
CMD ["/app"]
