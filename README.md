# Generated User Service (Go + gRPC + Protobuf)

## Overview

This project is a **gRPC-based User Service** implemented in **Go**, built from Protocol Buffer definitions.

It contains:

* `.proto` contract definition
* Generated `*.pb.go` files
* gRPC server implementation
* Service layer logic
* Domain model definitions

The service exposes user-related operations over **gRPC** and is structured for integration into a microservices architecture.

---

## Architecture

The service is built around gRPC communication:

```text
Client
  ↓
gRPC Server (User Service)
  ↓
Business Logic
```

The contract between client and server is defined in:

```text
proto/user.proto
```

Generated Go files provide strongly-typed request and response handling.

---

## Project Structure

```text
apis-gen-user-service-master/
│
├── cmd/
│   └── main.go
│
├── proto/
│   ├── user.proto
│   └── generated *.pb.go files
│
├── internal/
│   ├── service/
│   │   └── user_service.go
│   └── model/
│       └── user.go
│
├── go.mod
└── go.sum
```

---

## gRPC Contract

Defined in:

```text
proto/user.proto
```

The proto file defines:

* User service name
* RPC methods
* Request messages
* Response messages
* User message structure

After compilation, the generated `.pb.go` files are used by the server implementation.

---

## Core Domain Model

### User

Defined in:

```text
internal/model/user.go
```

Typical fields include:

* ID
* Name
* Email
* Password
* CreatedAt

Business logic for user operations is implemented in:

```text
internal/service/user_service.go
```

---

## How to Run

### 1. Clone repository

```bash
git clone <your-repository-url>
cd apis-gen-user-service-master
```

### 2. Install dependencies

```bash
go mod tidy
```

### 3. Run the service

```bash
go run cmd/main.go
```

The service starts a gRPC server listening on the port defined in `main.go`.

---

## Regenerating Protobuf Files (If Needed)

If you modify `user.proto`, regenerate the Go files using:

```bash
protoc --go_out=. --go-grpc_out=. proto/user.proto
```

Make sure `protoc` and Go gRPC plugins are installed.

---

## Technologies Used

* Go
* gRPC
* Protocol Buffers
* Modular service structure

---

## What This Project Demonstrates

* gRPC server implementation in Go
* Protobuf contract design
* Strongly-typed RPC communication
* Structured microservice architecture
* Separation between transport and business logic
