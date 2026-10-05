# Authorization

## Overview

Authorization in the platform is implemented using session verification and role-aware route protection.

## Student Authorization

Student access is protected in the student dashboard app.

Relevant files:

- `websitandStudent_Dashboard_Frontend/src/app/student-dashboard/components/ProtectedRoute.tsx`
- `websitandStudent_Dashboard_Frontend/src/app/student-dashboard/contexts/UserContext.tsx`
- `ucambridge_backend/student/check_auth.php`

The student app checks:

- whether the session exists
- whether the user is authenticated
- whether the dashboard should render protected content or redirect

## Teacher Authorization

Teacher routes are protected within the teacher dashboard application.

Relevant files:

- `Teacher_Dashboard_Frontend/src/App.tsx`
- `Teacher_Dashboard_Frontend/src/contexts/AuthContext.tsx`
- `ucambridge_backend/teacher/check_auth.php`

The teacher app ensures the user is authenticated before the teacher dashboard view is rendered.

## Admin Authorization

The admin app contains the most explicit authorization logic.

Relevant files:

- `Admin_Dashboard_Frontend/src/components/auth/ProtectedRoute.tsx`
- `Admin_Dashboard_Frontend/src/services/authService.ts`

### Verified admin permission model

The admin frontend checks:

- `authService.isAuthenticated()`
- `authService.checkAuth()`
- `authService.canAccessPage(pageId)`
- `authService.hasPermission(pageId, action)`

The permission metadata includes:

- `accessible_pages`
- `permissions`
- `is_super_admin`

### Page mapping

The admin route guard maps route paths to permission IDs and redirects the user when access is denied.

This is a real permission-aware layer in the codebase and is not a simple visual-only restriction.

## Admin Page Access Model

The observable model is:

- route to page ID mapping
- page ID to first accessible route mapping
- permission check before route rendering
- redirect to default allowed route when access is denied

## Authorization Summary

| Role | Authorization model |
|------|---------------------|
| Student | Session-based protected route and backend check |
| Teacher | Session-based protected dashboard and backend check |
| Admin | Session-based auth + page permission checks + route guard |

## Important Detail

The admin authorization layer is stronger than the student or teacher route guards because it uses page-level and action-level permission metadata in addition to authentication status.
