## Overview
- **Status:** In Review / Brainstorm

## Functional Requirements
- [ ] **F01:** The system **must** allow a user to create a new trigger, capturing the creation timestamp and a description of the event.
- [ ] **F02:** The system **must** allow a user to register custom core themes within their profile.
- [ ] **F03:** The system **must** allow a user to link their registered core themes to a specific trigger.
- [ ] **F04:** The system **must** allow a user to add generic emotions to a trigger.
- [ ] **F05:** The system **should** allow a user to rank the intensity of the triggered episode. 
                *(Note: Specify if this is a single overall ranking per trigger, rather than ranking each individual emotion).*
- [ ] **F06:** The system **must** allow a user to view a previously registered trigger.
- [ ] **F07:** The system **must** allow a user to edit a previously registered trigger.
                *(limited to the description, caption, thoughts, triggered emotions, triggered core themes, and reaction).*
- [ ] **F08:** The system **must** allow a user to delete an existing trigger permanently Fom the database.
- [ ] **F09:** The system **should** generate different statistics   based on the registered emotions. 
                *(Note: Define specific statistical views and prioritize them).*
- [ ] **F10:** The system **should** provide a login feature for users with a username and credentials.
- [ ] **F11:** The system **could** integrate a "feelings wheel" UI component for selecting emotions.

## Non-Functional Requirements
- [ ] **NF01:** **Privacy:** The system **must** minimize data collection, only storing information crucial for the application's functionality.
- [ ] **NF02:** **Data Control:** The system **must** allow users to completely delete their data upon request.
- [ ] **NF03:** **Security:** Passwords **must** be securely hashed prior to database storage.
- [ ] **NF04:** **Usability:** The interface **should** be intuitive and easy to use.
- [ ] **NF05:** **Maintainability:** The codebase **should** follow a clean architecture to ensure it is easy to upscale and maintain.

## Design considerations

### Intensity Rating (F05)
Should the user rate each emotion, or just give the whole event one overall score? To keep the MVP simple and avoid too many inputs, I will probably stick to **one overall 1-10 score per trigger event**.

### Stats & Charts (F09)
What charts actually bring value? For example: "Most common emotions this month" or "Which core themes cause the most triggers". I need to figure out exactly which stats to build first when I design the backend.

### Login & Database Setup
Since triggers connect directly to both emotions and core themes, a relational database like **PostgreSQL** or **SQLite** makes the most sense. It will make handling the relationships between tables a lot easier than using NoSQL.
