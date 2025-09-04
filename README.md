# StudioFS Database Schema

This repository contains the shared Protocol Buffers schema definitions for the StudioFS distributed filesystem ecosystem.

## Overview

The StudioFS database schema defines the structure for:
- Filesystem configuration metadata
- S3 storage configuration
- Chunk configuration settings
- Runtime statistics

This schema is shared across multiple StudioFS applications:
- `studiofs-lobby` - Administrative CLI utility
- `studiofs-artist` - Client application
- Other StudioFS ecosystem components

## Schema Files

- `sfs.proto` - Main Protocol Buffers schema definition
- `sfs.pb.go` - Generated Go code (auto-generated)

## Usage

### Go Projects

Add to your `go.mod`:
```go
require github.com/valandreev/studiofs-db-schema v0.1.0
```

Import in your Go code:
```go
import sfs_proto "github.com/valandreev/studiofs-db-schema"
```

### Generating Code

To regenerate Go code from the protobuf schema:

```bash
protoc --go_out=. --go_opt=paths=source_relative sfs.proto
```

## Schema Structure

### FilesystemConfig
Primary configuration object for filesystem instances containing:
- Unique filesystem identifier (UUID)
- Human-readable name
- Creation timestamp
- S3 storage configuration
- Chunk configuration parameters

### S3Config
S3-compatible storage configuration:
- Endpoint URL
- Bucket name
- Access credentials
- Region settings

### ChunkConfig
Data chunking parameters:
- Maximum chunk size in MB

### FilesystemStats
Runtime statistics (updated by sfs-artist client):
- File and directory counts
- Total size information
- Last updated timestamp

## Versioning

This repository uses semantic versioning. Breaking changes to the protobuf schema will result in major version bumps.

## License

[Specify license here]
