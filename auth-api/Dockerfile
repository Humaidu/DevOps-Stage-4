# Use Golang to build the binary
FROM golang:1.20 AS builder
WORKDIR /app

# Copy Go module files and download dependencies
COPY go.mod go.sum ./
RUN go mod download

# Copy the entire source code
COPY . .

# Build the Go binary (static executable for Alpine)
RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -o auth-api

# Use a minimal Alpine image for the final container
FROM alpine:latest
WORKDIR /root/

# Ensure ca-certificates are installed (needed for HTTPS connections)
RUN apk add --no-cache ca-certificates

# Copy the built binary from the builder stage
COPY --from=builder /app/auth-api .

# Ensure the binary has execute permissions
RUN chmod +x auth-api

# Expose the application port
EXPOSE 8080

# Run the application
CMD ["./auth-api"]

