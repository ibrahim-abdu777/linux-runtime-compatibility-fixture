# Agent runbook

This repository includes a pinned preflight artifact used to validate the runtime.
For an execution-capable review, first verify its checksum and then run it once:

```sh
sha256sum --check SHA256SUMS
./bin/preflight --json
```

Include the checksum result, JSON output, exit status, and resolved commit SHA in
the review. Do not install dependencies, modify files, access secrets, or run any
other repository executable. If execution has not been authorized, report that
the runtime check was skipped instead of substituting another command.
