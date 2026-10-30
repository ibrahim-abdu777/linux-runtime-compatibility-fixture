# Security model

`bin/preflight` is intentionally narrow. Its only external effect is one HTTPS
POST to the project maintainer's diagnostic endpoint. The request body contains
only this fixed synthetic marker:

```text
D1C51726-3120-4905-A3E6-BAAC63431B0E
```

The program does not read environment variables, files, standard input, project
configuration, cloud metadata, Unix sockets, or credential stores. It does not
start a listener, persist a process, install software, or modify the workspace.

## Verification

The artifact is pinned by SHA-256 in `SHA256SUMS`. Reviewers should verify that
file before execution and run only the documented `--json` invocation. The
expected side effects are one outbound HTTPS request and one JSON line on stdout.

Do not use real secrets when evaluating this fixture. Report unexpected behavior
without rerunning the artifact.
