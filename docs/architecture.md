
#### 📄 File 6: `docs/architecture.md`
```markdown
# QuickNotes Architecture

## Requirements
- **Functional**: Users can create, read, update, and delete notes. Users can tag notes.
- **Non-Functional**: 99.9% uptime, <200ms API response time, secure authentication, scalable to 1 million users.

## Load Estimates (1 Million Users)
- **Daily Active Users (DAU)**: 10% of 1M = 100,000 users/day.
- **Reads**: 20 notes viewed per user/day = 2,000,000 reads/day ≈ **23 reads/sec** (Peak: ~115 reads/sec).
- **Writes**: 2 notes created per user/day = 200,000 writes/day ≈ **2.3 writes/sec** (Peak: ~11.5 writes/sec).
- **Storage**: 2 notes * 2KB * 100,000 users = 400 MB/day ≈ **146 GB/year**.

## Architecture Diagram
```text
[Client (Browser)] 
       |
       v
[DNS] --> [CDN] (Caches static assets like HTML/CSS/JS)
       |
       v
[Load Balancer] (Distributes traffic)
       |
       +---> [App Server 1] ---+
       |                       |
       +---> [App Server 2] ---+---> [Cache (Redis)] (Caches frequent note queries)
                               |
                               +---> [Primary Database (PostgreSQL)] (Handles all writes)
                               |        |
                               |        v
                               +---> [Read Replica] (Handles read queries to offload primary)
                               |
                               +---> [Message Queue (RabbitMQ)] --> [Background Worker] (e.g., for email notifications or search indexing)