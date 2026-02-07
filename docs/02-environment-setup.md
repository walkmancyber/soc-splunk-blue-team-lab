### Splunk Startup Verification

Splunk was started using Docker Compose and verified by:
- Checking running containers with `docker ps`
- Reviewing startup logs via `docker logs`
- Accessing the web interface at http://localhost:8000

### Splunk License Acceptance

Recent versions of Splunk require accepting both the license and the
Splunk General Terms using the SPLUNK_GENERAL_TERMS environment variable.
