# dnf-interceptor
Fast and simple to setup RPM mirror server for caching commonly downloaded packages in a self-hosted manner

### Use Case
For developers and contributors that need quick access to build and test in fresh and clean installs.
- E2E Testing will Ansible based environments
- Terraform IAC E2E

### Architecture
```
Server: VM
- /etc/hosts must be reconfigured with the Cache server. The Cache server will automatically proxy
  requests to RPM Mirrors if there is nocache hit
Cache:
- The cache must have access to the desired regional mirrors

Package Initial Download
+-------------+-------+-------------+
|   Server    | Cache |   Mirror    |
+-------------+-------+-------------+
| RPM Package | ?     | RPM Package |
+-------------+-------+-------------+

Second Package Hit
+-------------+----------+-------------+
|   Server    |  Cache   |   Mirror    |
+-------------+----------+-------------+
| RPM Package | (Cached) | RPM Package |
+-------------+----------+-------------+
```

### Benifits
- Reduce the need of having to host an entire mirror
- Have quick access to quick package installs when testing building out new infrastructure

