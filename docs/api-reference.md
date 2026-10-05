# API Reference

## Overview

The project exposes a role-based PHP endpoint API. The active implementation is direct PHP endpoint access rather than a centralized Express, Laravel, or Node router.

## Student API

| Endpoint | Method | Purpose | Authentication |
|----------|--------|---------|----------------|
| `/student/login.php` | POST | Student login | Session-based |
| `/student/check_auth.php` | GET | Check active session | Session-based |
| `/student/logout.php` | POST | Logout | Session-based |
| `/student/register.php` | POST | Student registration | Not verified as protected |
| `/student/check_email.php` | POST | Email validation | Not verified |
| `/student/verify_email.php` | POST | Email verification | Not verified |
| `/student/verify_otp.php` | POST | OTP verification | Not verified |
| `/student/placement_test.php` | POST/GET | Placement test | Session-based |
| `/student/get_enrolled_courses.php` | GET | Get student course list | Session-based |
| `/student/get_course_materials.php` | GET | Get course materials | Session-based |
| `/student/get_reports.php` | GET | Get student reports | Session-based |
| `/student/get_certificates.php` | GET | Get student certificates | Session-based |
| `/student/update_profile.php` | POST | Update profile | Session-based |

## Teacher API

| Endpoint | Method | Purpose | Authentication |
|----------|--------|---------|----------------|
| `/teacher/login.php` | POST | Teacher login | Session-based |
| `/teacher/check_auth.php` | GET | Validate teacher session | Session-based |
| `/teacher/logout.php` | POST | Teacher logout | Session-based |
| `/teacher/get_courses.php` | GET | Get teacher courses | Session-based |
| `/teacher/get_course_details.php` | GET | Get course details | Session-based |
| `/teacher/get_assignments.php` | GET | Teacher assignments | Session-based |
| `/teacher/get_materials.php` | GET | Material data | Session-based |
| `/teacher/teacher_details.php` | GET | Teacher details | Session-based |
| `/teacher/stream_course.php` | GET | Course streaming data | Session-based |

## Admin API

| Endpoint | Method | Purpose | Authentication |
|----------|--------|---------|----------------|
| `/admin/login.php` | POST | Admin login | Session-based |
| `/admin/check_auth.php` | GET | Validate admin session | Session-based |
| `/admin/logout.php` | POST | Admin logout | Session-based |
| `/admin/get_dashboard_stats.php` | GET | Dashboard statistics | Session-based |
| `/admin/...` | Various | Admin management endpoints | Session-based |

## Shared API Characteristics

- All actual verified auth is session-based
- Frontend requests include cookies via `credentials: 'include'`
- Responses are returned as JSON
- Backend logic is implemented in PHP files directly rather than a framework router

## Important Note

This document includes only the endpoints that were directly verified in the inspected codebase. Unverified or guessed endpoints are intentionally omitted.
