# Student-Industry-Faculty Bridge Platform API Documentation

## Overview

This documentation covers the complete API endpoints for the Student-Industry-Faculty Bridge Platform. The API provides comprehensive functionality for user management, opportunities, applications, mentorship, notifications, and file management.

## Base URL
```
https://yourdomain.com/api
```

## Authentication

All API requests require authentication via session cookies or API tokens.

### Headers
```
Content-Type: application/json
X-Requested-With: XMLHttpRequest
Authorization: Bearer <token> (if using API tokens)
```

## Response Format

All API responses follow this standard format:

```json
{
    "success": true|false,
    "data": {...},
    "error": "Error message (if success is false)",
    "meta": {
        "timestamp": "2024-01-01T00:00:00Z",
        "version": "1.0"
    }
}
```

## Authentication Endpoints

### POST /api/auth/login
Login a user with email and password.

**Request:**
```json
{
    "email": "user@example.com",
    "password": "password123"
}
```

**Response:**
```json
{
    "success": true,
    "data": {
        "user": {
            "id": 1,
            "name": "John Doe",
            "email": "user@example.com",
            "role": "student",
            "verified": true
        },
        "token": "jwt_token_here"
    }
}
```

### POST /api/auth/register
Register a new user.

**Request:**
```json
{
    "name": "John Doe",
    "email": "user@example.com",
    "password": "password123",
    "role": "student",
    "institution": "University Name"
}
```

### POST /api/auth/logout
Logout the current user.

### POST /api/auth/forgot-password
Request password reset.

**Request:**
```json
{
    "email": "user@example.com"
}
```

### POST /api/auth/reset-password
Reset password with token.

**Request:**
```json
{
    "token": "reset_token",
    "password": "new_password123"
}
```

## User Management Endpoints

### GET /api/users
Get all users (admin only).

**Query Parameters:**
- `page` (int): Page number
- `limit` (int): Results per page
- `role` (string): Filter by role
- `search` (string): Search by name or email

### GET /api/users/{id}
Get user by ID.

### PUT /api/users/{id}
Update user information.

**Request:**
```json
{
    "name": "Updated Name",
    "bio": "Updated bio",
    "skills": "JavaScript,PHP,React",
    "location": "City, Country"
}
```

### DELETE /api/users/{id}
Delete user (admin only).

### GET /api/users/{id}/profile
Get complete user profile.

### POST /api/users/{id}/follow
Follow/unfollow a user.

## Opportunity Endpoints

### GET /api/opportunities
Get all opportunities.

**Query Parameters:**
- `page` (int): Page number
- `limit` (int): Results per page
- `type` (string): internship, job, project
- `category` (string): Filter by category
- `location` (string): Filter by location
- `company` (string): Filter by company
- `skills` (string): Filter by skills (comma-separated)
- `sort` (string): date, relevance, company

**Response:**
```json
{
    "success": true,
    "data": {
        "opportunities": [
            {
                "id": 1,
                "title": "Software Development Intern",
                "description": "Full description...",
                "company_name": "Tech Corp",
                "location": "New York, NY",
                "type": "internship",
                "category": "technology",
                "skills_required": "JavaScript,React,Node.js",
                "requirements": "Requirements...",
                "benefits": "Benefits...",
                "application_deadline": "2024-12-31",
                "created_at": "2024-01-01T00:00:00Z"
            }
        ],
        "pagination": {
            "current_page": 1,
            "total_pages": 10,
            "per_page": 20,
            "total": 200
        }
    }
}
```

### GET /api/opportunities/{id}
Get opportunity by ID.

### POST /api/opportunities
Create new opportunity (industry role required).

**Request:**
```json
{
    "title": "Software Development Intern",
    "description": "Full description of the opportunity",
    "type": "internship",
    "category": "technology",
    "location": "New York, NY",
    "skills_required": "JavaScript,React,Node.js",
    "requirements": "Requirements for applicants",
    "benefits": "Benefits offered",
    "application_deadline": "2024-12-31",
    "is_remote": false,
    "salary_range": "50000-70000"
}
```

### PUT /api/opportunities/{id}
Update opportunity.

### DELETE /api/opportunities/{id}
Delete opportunity.

### GET /api/opportunities/{id}/applications
Get applications for an opportunity.

## Application Endpoints

### GET /api/applications
Get user's applications.

**Query Parameters:**
- `status` (string): pending, approved, rejected
- `type` (string): Filter by opportunity type

### GET /api/applications/{id}
Get application by ID.

### POST /api/applications
Submit new application.

**Request:**
```json
{
    "opportunity_id": 1,
    "cover_letter": "Dear hiring manager...",
    "resume_url": "/uploads/resume.pdf",
    "portfolio_url": "https://myportfolio.com",
    "additional_documents": [
        "/uploads/transcript.pdf",
        "/uploads/certificate.pdf"
    ]
}
```

### PUT /api/applications/{id}
Update application.

### DELETE /api/applications/{id}
Withdraw application.

### POST /api/applications/{id}/review
Review application (industry role required).

**Request:**
```json
{
    "status": "approved",
    "feedback": "Great application! Looking forward to working with you.",
    "interview_scheduled": "2024-02-15T10:00:00Z"
}
```

## Mentorship Endpoints

### GET /api/mentorship/requests
Get mentorship requests.

### POST /api/mentorship/requests
Send mentorship request.

**Request:**
```json
{
    "mentor_id": 5,
    "message": "I would like to request mentorship in web development",
    "goals": "Learn React and Node.js",
    "duration": "3 months"
}
```

### PUT /api/mentorship/requests/{id}
Update mentorship request status.

**Request:**
```json
{
    "status": "accepted",
    "response_message": "I'd be happy to mentor you!"
}
```

### GET /api/mentorship/sessions
Get mentorship sessions.

### POST /api/mentorship/sessions
Schedule mentorship session.

**Request:**
```json
{
    "mentorship_id": 1,
    "scheduled_at": "2024-02-15T14:00:00Z",
    "duration": 60,
    "topic": "React Fundamentals",
    "meeting_link": "https://zoom.us/j/123456789"
}
```

## Notification Endpoints

### GET /api/notifications
Get user notifications.

**Query Parameters:**
- `unread` (boolean): Filter unread notifications
- `type` (string): Filter by notification type

**Response:**
```json
{
    "success": true,
    "data": {
        "notifications": [
            {
                "id": 1,
                "type": "application_status",
                "title": "Application Approved",
                "message": "Your application for Software Developer position has been approved",
                "read": false,
                "created_at": "2024-01-01T10:00:00Z",
                "data": {
                    "application_id": 5,
                    "opportunity_id": 3
                }
            }
        ],
        "unread_count": 5
    }
}
```

### POST /api/notifications/send
Send notification (admin/system use).

**Request:**
```json
{
    "user_id": 1,
    "type": "system",
    "title": "System Maintenance",
    "message": "System will be under maintenance from 2-4 PM",
    "send_email": true
}
```

### PUT /api/notifications/{id}/read
Mark notification as read.

### PUT /api/notifications/mark-all-read
Mark all notifications as read.

### GET /api/notifications/preferences
Get notification preferences.

### PUT /api/notifications/preferences
Update notification preferences.

**Request:**
```json
{
    "email_notifications": true,
    "push_notifications": false,
    "application_updates": true,
    "mentorship_updates": true,
    "system_announcements": false
}
```

## File Management Endpoints

### POST /api/files/upload
Upload file(s).

**Request (multipart/form-data):**
```
file: [File object]
category: "resume" | "portfolio" | "document" | "image"
```

**Response:**
```json
{
    "success": true,
    "data": {
        "files": [
            {
                "id": 1,
                "filename": "resume.pdf",
                "original_name": "John_Doe_Resume.pdf",
                "file_path": "/uploads/2024/01/resume_abc123.pdf",
                "file_size": 245760,
                "mime_type": "application/pdf",
                "category": "resume",
                "uploaded_at": "2024-01-01T10:00:00Z"
            }
        ]
    }
}
```

### GET /api/files/{id}
Get file information.

### GET /api/files/{id}/download
Download file.

### DELETE /api/files/{id}
Delete file.

### GET /api/files/user/{user_id}
Get user's files.

### GET /api/files/stats
Get file upload statistics.

## Search Endpoints

### POST /api/search
Perform search across platform.

**Request:**
```json
{
    "query": "javascript developer",
    "filters": {
        "type": ["opportunity", "user"],
        "category": ["technology"],
        "location": ["New York"],
        "skills": ["JavaScript", "React"]
    },
    "sort": "relevance",
    "page": 1,
    "per_page": 20,
    "include_facets": true
}
```

**Response:**
```json
{
    "success": true,
    "data": {
        "results": [
            {
                "id": 1,
                "type": "opportunity",
                "title": "JavaScript Developer",
                "description": "Looking for experienced JavaScript developer...",
                "score": 0.95,
                "highlighted": {
                    "title": "<mark>JavaScript</mark> Developer",
                    "description": "Looking for experienced <mark>JavaScript</mark> <mark>developer</mark>..."
                }
            }
        ],
        "facets": {
            "categories": [
                {"value": "technology", "label": "Technology", "count": 45},
                {"value": "marketing", "label": "Marketing", "count": 12}
            ],
            "skills": [
                {"value": "javascript", "label": "JavaScript", "count": 30},
                {"value": "react", "label": "React", "count": 25}
            ]
        },
        "stats": {
            "total": 150,
            "search_time": 45
        },
        "pagination": {
            "current_page": 1,
            "total_pages": 8,
            "per_page": 20,
            "total": 150
        }
    }
}
```

### POST /api/search/advanced
Perform advanced search with complex filters.

## Analytics Endpoints

### GET /api/analytics/dashboard
Get dashboard analytics.

**Response:**
```json
{
    "success": true,
    "data": {
        "total_users": 1250,
        "total_opportunities": 340,
        "total_applications": 890,
        "active_mentorships": 45,
        "recent_activity": [
            {
                "type": "new_user",
                "count": 12,
                "date": "2024-01-01"
            }
        ],
        "user_growth": [
            {"month": "2024-01", "count": 100},
            {"month": "2024-02", "count": 150}
        ]
    }
}
```

### GET /api/analytics/applications
Get application analytics.

### GET /api/analytics/opportunities
Get opportunity analytics.

### GET /api/analytics/users
Get user analytics.

## Certificate Endpoints

### GET /api/certificates
Get user certificates.

### POST /api/certificates
Issue certificate.

**Request:**
```json
{
    "user_id": 1,
    "type": "completion",
    "title": "Web Development Internship Completion",
    "description": "Successfully completed 3-month web development internship",
    "issued_by": "Tech Corp",
    "skills_verified": ["JavaScript", "React", "Node.js"]
}
```

### GET /api/certificates/{id}
Get certificate details.

### GET /api/certificates/{id}/verify
Verify certificate authenticity.

## Error Codes

| Code | Description |
|------|-------------|
| 400 | Bad Request - Invalid request data |
| 401 | Unauthorized - Authentication required |
| 403 | Forbidden - Insufficient permissions |
| 404 | Not Found - Resource not found |
| 422 | Unprocessable Entity - Validation failed |
| 429 | Too Many Requests - Rate limit exceeded |
| 500 | Internal Server Error - Server error |

## Rate Limiting

API requests are rate limited:
- 1000 requests per hour for authenticated users
- 100 requests per hour for unauthenticated users
- 50 requests per minute per endpoint

## Pagination

Most list endpoints support pagination:

**Query Parameters:**
- `page` (int, default: 1): Page number
- `limit` (int, default: 20, max: 100): Items per page

**Response includes:**
```json
{
    "pagination": {
        "current_page": 1,
        "total_pages": 10,
        "per_page": 20,
        "total": 200,
        "has_next": true,
        "has_prev": false
    }
}
```

## Filtering and Sorting

Many endpoints support filtering and sorting:

**Common Filter Parameters:**
- `search` (string): Full-text search
- `status` (string): Filter by status
- `type` (string): Filter by type
- `date_from` (date): Filter from date
- `date_to` (date): Filter to date

**Common Sort Parameters:**
- `sort` (string): Field to sort by
- `order` (string): asc or desc

## WebSocket Events

Real-time events via WebSocket:

### Connection
```javascript
const ws = new WebSocket('wss://yourdomain.com/ws');
```

### Events
- `notification.new`: New notification received
- `application.status_changed`: Application status updated
- `mentorship.message`: New mentorship message
- `system.announcement`: System announcement

## SDKs and Libraries

### JavaScript SDK
```javascript
import { StudentBridgeAPI } from 'student-bridge-sdk';

const api = new StudentBridgeAPI({
    baseURL: 'https://yourdomain.com/api',
    token: 'your_api_token'
});

// Usage
const opportunities = await api.opportunities.list({
    type: 'internship',
    category: 'technology'
});
```

### PHP SDK
```php
use StudentBridge\API\Client;

$client = new Client([
    'base_url' => 'https://yourdomain.com/api',
    'token' => 'your_api_token'
]);

// Usage
$opportunities = $client->opportunities()->list([
    'type' => 'internship',
    'category' => 'technology'
]);
```

## Testing

### Test Environment
```
Base URL: https://test.yourdomain.com/api
```

### Sample Data
Test environment includes sample users, opportunities, and applications for testing.

### Postman Collection
Download our Postman collection: [Student Bridge API.postman_collection.json](https://yourdomain.com/api/docs/postman)

## Support

For API support:
- Email: api-support@yourdomain.com
- Documentation: https://docs.yourdomain.com
- Status Page: https://status.yourdomain.com

## Changelog

### v1.0.0 (2024-01-01)
- Initial API release
- All core endpoints implemented
- Authentication and authorization
- File upload functionality
- Search and analytics
- Real-time notifications