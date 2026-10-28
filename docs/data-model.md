
#### 📄 File 5: `docs/data-model.md`
```markdown
# QuickNotes Data Model

## Entities and Relationships
- **users**: Stores user account information.
- **notes**: Stores the note content. Relationship: One-to-Many with `users` (one user has many notes).
- **tags**: Stores tag names. Relationship: Many-to-Many with `notes` (a note can have many tags, a tag can belong to many notes).
- **note_tags**: Junction table resolving the many-to-many relationship between `notes` and `tags`.

## CREATE TABLE Statements
```sql
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    username VARCHAR(50) UNIQUE NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE notes (
    id SERIAL PRIMARY KEY,
    user_id INT NOT NULL REFERENCES users(id) ON DELETE CASCADE,
    title VARCHAR(100) NOT NULL,
    body TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE tags (
    id SERIAL PRIMARY KEY,
    name VARCHAR(50) UNIQUE NOT NULL
);

CREATE TABLE note_tags (
    note_id INT REFERENCES notes(id) ON DELETE CASCADE,
    tag_id INT REFERENCES tags(id) ON DELETE CASCADE,
    PRIMARY KEY (note_id, tag_id)
);