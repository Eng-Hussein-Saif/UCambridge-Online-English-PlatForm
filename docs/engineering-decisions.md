# Engineering Decisions

## Why multiple frontends?

The project uses separate frontend applications for public, student, teacher, and admin experiences. This model allows the platform to separate user contexts while still sharing one backend system.

## Why role-based separation?

The backend and frontend are organized around user role modules. This keeps authentication and authorization logic more explicit and easier to manage.

## Why PHP sessions?

The actual backend uses PHP sessions and cookie-based state, which matches the verified implementation. This is consistent with the current backend auth flow and is the correct documented model.

## Why endpoint-based backend?

The code is structured as role-based PHP endpoint files rather than a framework-specific router. This creates a straightforward API service architecture with direct logic per user role.

## How admin permissions are enforced

The admin dashboard includes permission-aware route guards and access checks. The app checks page-level permissions before rendering what the user may access.

## Challenges and solutions

### Multi-app architecture

Challenge: separate frontends require strong API contract discipline.

Solution: centralized backend with role-specific endpoints.

### Session-based auth across apps

Challenge: cookies and session validation must be preserved across multiple client apps.

Solution: each frontend uses credentials-included requests and server-side session checks.

### Permission enforcement

Challenge: UI-only restrictions are not enough.

Solution: backend session validation and frontend page permission logic. The admin dashboard implements explicit permission checks.

### Legacy/mock coexistence

Challenge: legacy code or demo logic may coexist with active logic.

Solution: focus documentation on the verified production implementation paths rather than older or mock flows.

## Conclusion

The project’s engineering decisions are consistent with a real multi-role learning platform: role separation, PHP backend, MySQL persistence, and permission-aware dashboard boundaries.
