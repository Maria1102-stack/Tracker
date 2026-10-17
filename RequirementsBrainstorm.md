## Overview
- **Status:** In Review / Brainstorm

## Functional Requirements
- [ ] **F01:** The system **must** allow a user to create a new trigger, capturing the creation timestamp and a description of the event.
- [ ] **F02:** The system **must** allow a user to register custom core themes within their profile.
- [ ] **F03:** The system **must** allow a user to link their registered core themes to a specific trigger.
- [ ] **F04:** The system **must** allow a user to add generic emotions to a trigger.
- [ ] **F05:** The system **should** allow a user to rank the intensity of the triggered episode. 
- [ ] **F06:** The system **must** allow a user to view a previously registered trigger.
- [ ] **F07:** The system **must** allow a user to edit a previously registered trigger. Editing is limited to the description, caption, thoughts, triggered emotions, triggered core themes, and reaction
- [ ] **F08:** The system **must** allow a user to delete an existing trigger permanently Fom the database.
- [ ] **F09:** The system **should** generate different statistics based on the registered emotions. 
- [ ] **F10:** The system **should** provide a login feature for users with a username and credentials.
- [ ] **F11:** The system **could** integrate a "feelings wheel" UI component for selecting emotions.

## Non-Functional Requirements *(Must all be measureable )*
- [ ] **NF01:** **Privacy:** The system **must** minimize data collection, only storing information crucial for the application's functionality.
- [ ] **NF02:** **Data Control:** The system **must** allow users to completely delete their data upon request.
- [ ] **NF03:** **Security:** Passwords **must** be securely hashed prior to database storage.
- [ ] **NF04:** **Usability:** The user interface **should** be intuitive and easy to use.
- [ ] **NF05:** **Maintainability:** The codebase **should** follow a clean architecture to ensure it is easy to upscale and maintain.

## Design considerations

### Intensity Rating (F05)
Should the user rate each emotion, or just give the whole event one overall score? To keep the MVP simple and avoid too many inputs, I will probably stick to **one overall 1-10 score per trigger event**.

### Stats & Charts (F09)
What charts actually bring value? For example: "Most common emotions this month" or "Which core themes cause the most triggers". I need to figure out exactly which stats to build first when I design the backend.

### Login & Database Setup
Since triggers connect directly to both emotions and core themes, a relational database like PostgreSQL or SQLite makes the most sense. It will make handling the relationships between tables a lot easier than using NoSQL.

However, choosing the right database structure depends on the future cross-platform requirement:
* **Option A (Local-First):** Use SQLite for a mobile/desktop app. To support cross-platform sync without hosting a backend, look into letting users sync via their personal cloud (e.g., iCloud, Google Drive) or tools like *CR-SQLite* / *ElectricSQL*. This heavily aligns with **NF01 (Privacy)**.
* **Option B (Cloud-Based Relational):** Use a hosted PostgreSQL database (via Supabase or similar) combined with user authentication (**F10**). If this route is chosen, data encryption at rest or end-to-end encryption must be considered to uphold the strict privacy standards in **NF01**.
