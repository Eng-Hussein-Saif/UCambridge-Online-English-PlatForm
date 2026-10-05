# Data Flows

## Student Login Flow

```mermaid
sequenceDiagram
    participant Stu as Student Frontend
    participant BE as PHP Backend
    participant DB as MySQL
    participant S as Session

    Stu->>BE: POST /student/login.php
    BE->>DB: Validate student record
    DB-->>BE: User result
    BE->>S: Set session variables
    BE-->>Stu: JSON login success
    Stu->>BE: GET /student/check_auth.php
    BE->>S: Validate active session
    BE-->>Stu: Authenticated payload
```

## Teacher Login Flow

```mermaid
sequenceDiagram
    participant Tea as Teacher Frontend
    participant BE as PHP Backend
    participant DB as MySQL
    participant S as Session

    Tea->>BE: POST /teacher/login.php
    BE->>DB: Validate teacher record
    DB-->>BE: Teacher result
    BE->>S: Create teacher session
    BE-->>Tea: JSON success response
```

## Admin Login + Permission Flow

```mermaid
sequenceDiagram
    participant Admin as Admin Frontend
    participant BE as PHP Backend
    participant DB as MySQL
    participant S as Session

    Admin->>BE: POST /admin/login.php
    BE->>DB: Validate admin user
    DB-->>BE: Admin record
    BE->>S: Store session + permissions
    BE-->>Admin: JSON success
    Admin->>BE: GET /admin/check_auth.php
    BE->>S: Validate session
    BE-->>Admin: Auth + page permissions
    Admin->>Admin: Route guard checks page access
```

## Student Retrieves Data

```mermaid
sequenceDiagram
    participant Stu as Student Dashboard
    participant BE as PHP Backend
    participant DB as MySQL

    Stu->>BE: Request student data endpoint
    BE->>DB: Query student profile / course info
    DB-->>BE: Data payload
    BE-->>Stu: JSON response
```

## Teacher Retrieves Data

```mermaid
sequenceDiagram
    participant Tea as Teacher Dashboard
    participant BE as PHP Backend
    participant DB as MySQL

    Tea->>BE: Request teacher course data
    BE->>DB: Query teacher records
    DB-->>BE: Results
    BE-->>Tea: JSON response
```

## Admin Retrieves Data

```mermaid
sequenceDiagram
    participant Admin as Admin Dashboard
    participant BE as PHP Backend
    participant DB as MySQL

    Admin->>BE: Request admin management data
    BE->>DB: Query dashboard info / users / reports
    DB-->>BE: Result set
    BE-->>Admin: JSON payload
```

## Student Submits Data

The same pattern is used when a student submits assignments, feedback, or profile updates:

- frontend calls backend endpoint
- backend validates session
- backend updates or inserts rows in MySQL
- JSON response is returned

## Teacher Submits Data

Teacher updates to courses, materials, assignments, announcements, or reports follow the same pattern.

## Admin Modifies Data

Admin modifications to course, user, payment, announcement, and permission data follow the same backend + database model with stronger access checks.
