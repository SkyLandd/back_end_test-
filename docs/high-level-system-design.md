# High-Level Design

The game system (As per scope of the problem statement) consists of the below modules:

### 1. Authentication Module/Service

**Responsibilities:**

- User registration
- User login
- Request authentication
- Password hashing
- Email verification

### 2. Game Module

**Responsibilities:**

- Managing virtual maps
- Random treasure placements
- Game logic implementation
- Quests and challenges (assumed but not developed - might need another module where game module being an orchestrator)
- Exploration mechanics (assumed but not developed - might need another module where game module being an orchestrator)

### 3. Treasure Module

**Responsibilities:**

- Treasure management (types, values, rarities)
- Handling treasure collection
- Ensuring secure collection (preventing duplication or cheating)
- Storing treasure attributes (e.g., common, rare, epic, legendary)
- Daily/weekly limits management on treasure collection

### 4. Player Module

**Responsibilities:**

- Managing player-related information
- Tracking treasures collected by players
- Monitoring game progress
- Handling player statistics (e.g., total treasures collected, quests completed)
- Leaderboard management
- Trading treasures between players

<img src="High Level Architecture.drawio.png" width="492" height="228" alt="High Level Architecture and components">

High Level Architecture and components

---

### Endpoints:

### 1. Authentication Module/Service

- **Endpoints:**
    - `POST /register`
    - `POST /login`
    - `POST /verify-email`
- **Security:**
    - JWT for securing endpoints
    - bcrypt for password hashing
    - Email service for sending verification emails

### 2. Game Module

- **Endpoints:**
    - `GET /maps`  [Not in Scope - Keeping here for a high level completeness - There can be a seperate module also for managing this]
    - `POST /explore`[Not in Scope - Keeping here for a high level completeness - There can be a seperate module also for managing this]
    - `POST /collect-treasure`
    - `GET /quests`[Not in Scope - Keeping here for a high level completeness - There can be a seperate module also for managing this]
    - `POST /complete-quest`[Not in Scope - Keeping here for a high level completeness - There can be a seperate module also for managing this]
- **Logic:**
    - Random placement of treasures
    - Handling treasure collections

### 3. Treasure Module

- **Logic:**
    - Managing different types and rarities of treasures
    - Secure treasure collection processes by validation
    - Does not directly interact with outer system. Only for seperating treasure related logic.

### 4. Player Module

- **Endpoints:**
    - `GET /player/:id`
    - `GET /player/:id/statistics`
    - `GET /leaderboard`
    - `POST /trade-treasures`
- **Logic:**
    - Managing player statistics and progress
    - Handling trading between players
    - Updating and caching leaderboard for performance