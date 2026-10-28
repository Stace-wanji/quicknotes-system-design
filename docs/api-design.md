# QuickNotes API Design

## REST Endpoints
| Method | Path | Description | Success Status |
|--------|------|-------------|----------------|
| GET | `/notes` | List all notes for the authenticated user | 200 OK |
| POST | `/notes` | Create a new note | 201 Created |
| GET | `/notes/{id}` | Retrieve a specific note by ID | 200 OK |
| PUT | `/notes/{id}` | Update an existing note | 200 OK |
| DELETE | `/notes/{id}` | Delete a specific note | 204 No Content |
| GET | `/users/{userId}/notes` | List all notes for a specific user | 200 OK |

## JSON Examples

### Create a Note (POST /notes)
**Request Body:**
```json
{
  "title": "Meeting Notes",
  "body": "Discuss Q4 roadmap and budget.",
  "userId": 1
}