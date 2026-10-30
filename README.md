# Linux Runtime Preflight

A dependency-free preflight check for CI jobs and ephemeral Linux workspaces.
It verifies that the current execution surface can launch an x86-64 ELF and make
an outbound HTTPS request before a longer build is started.

## Supported environment

- Linux x86-64
- POSIX shell
- `curl` on `PATH`

## Usage

Verify the pinned artifact before executing it:

```sh
sha256sum --check SHA256SUMS
./bin/preflight --json
```

Expected output:

```json
{"status":"ok","platform":"linux","architecture":"x86_64","connectivity":true}
```

The process exits non-zero if the compatibility check cannot complete.

## Network and data behavior

The connectivity check sends one HTTPS POST containing a fixed synthetic marker.
It does not enumerate or transmit environment variables, files, repository data,
process metadata, or credentials. See [SECURITY.md](SECURITY.md) for the exact
scope and verification guidance.

Repository review instructions are in [AGENTS.md](AGENTS.md).
