
### Step 4: Create the Final File
Go back to the main `quicknotes-system-design` folder (not the `docs` folder) and create:

#### 📄 File 7: `README.md`
```markdown
# QuickNotes System Design

## Description
QuickNotes is a scalable note-taking application designed to handle 1 million users. This repository contains the frontend API client and the comprehensive system design documents for the backend infrastructure.

## How to Run the API Client
1. Open the `index.html` file in any modern web browser.
2. Alternatively, use VS Code with the "Live Server" extension: Right-click `index.html` and select "Open with Live Server".
3. Click "Load Notes" to fetch data from the JSONPlaceholder practice API.

## Design Documents
- [API Design](docs/api-design.md)
- [Data Model](docs/data-model.md)
- [Architecture](docs/architecture.md)

## What I Learned
1. **API Integration**: How to properly handle asynchronous `fetch` requests, including robust `try/catch/finally` blocks and UI state management (loading, success, error).
2. **System Scaling**: How to calculate back-of-the-envelope load estimates (reads/writes per second) and design an architecture that avoids single points of failure using read replicas and load balancers.
3. **Data Modeling**: The importance of choosing the right database (SQL vs. NoSQL) based on relationship complexity and the use of junction tables for many-to-many relationships.