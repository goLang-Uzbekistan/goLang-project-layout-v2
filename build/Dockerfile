# /build/docker/Dockerfile
FROM golang:1.23 AS builder

WORKDIR /app

# Copy go.mod and go.sum files
COPY go.mod go.sum ./

# Download dependencies
RUN go mod download

# Copy the source code
COPY . .

# Build the application
RUN go build -o myapp ./cmd/myapp

# Second stage: Build a minimal container
FROM gcr.io/distroless/base

WORKDIR /app

# Copy the built binary from the builder
COPY --from=builder /app/myapp .

# Run the application
CMD ["/app/myapp"]
