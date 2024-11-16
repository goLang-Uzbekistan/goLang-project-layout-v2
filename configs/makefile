# Makefile to manage Go project tasks

# Variables
APP_NAME := myapp
GO := go
BINARY := $(APP_NAME)

# Directories
SRCDIR := ./cmd/$(APP_NAME)
PKGDIR := ./pkg
INTDIR := ./internal
TESTDIR := ./test

.PHONY: all build clean test fmt vendor run

# Default target to run when no arguments are given
all: build

# Build the application
build:
	@echo "Building the application..."
	$(GO) build -o $(BINARY) $(SRCDIR)

# Run the application
run: build
	@echo "Running the application..."
	./$(BINARY)

# Clean up built files
clean:
	@echo "Cleaning up..."
	rm -f $(BINARY)

# Run tests
test:
	@echo "Running tests..."
	$(GO) test ./...

# Format the code
fmt:
	@echo "Formatting Go code..."
	$(GO) fmt ./...

# Vendor dependencies
vendor:
	@echo "Updating vendor directory..."
	$(GO) mod vendor