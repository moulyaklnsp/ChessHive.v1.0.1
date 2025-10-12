# ChessHive – Test Plan

## 1. Overview

This document outlines the testing plan for the *ChessHive Web Application, covering **Functional, **Validation, **UI, **Backend/API, and **Integration* testing.  
It includes test cases, expected outputs, and *sample API requests/responses* for backend verification.

---

## 2. Testing Scope

- *Functional Testing:* Verify user functionalities for Coordinators, Organizers, Players, and Admins.  
- *Validation Testing:* Check input constraints and form data correctness.  
- *UI Testing:* Confirm responsive layout and dynamic UI elements.  
- *API Testing:* Validate backend routes, JSON responses, and HTTP status codes.  
- *Integration Testing:* Ensure seamless data flow between frontend and backend components.

---

## 3. Roles & Responsibilities

| Role | Responsible Person | Testing Area |
|------|--------------------|---------------|
| Coordinator | P. Moulya | Tournament & Store modules, Pairings & Rankings UI |
| Organizer | Tejaswi | Product sales, College stats, Meetings, Sales analysis |
| Player | Vivash | Tournament joining, Product purchases, Growth analysis |
| Backend Developer | Neelukumar | Routes, APIs, Data handling, Static rendering |
| Admin | Ashlesha | Monitoring, Reports, and User management |

---

## 4. Test Cases

### 4.1 Validation Testing

| Test ID | Description | Steps | Expected Result | Status |
|----------|-------------|-------|----------------|--------|
| V-001 | Email validation | Enter invalid email in Login form | Error: “Invalid email format.” | ✅ Passed |
| V-002 | Password strength check | Signup with weak password | Error: “Password must include 8+ chars, uppercase, number.” | ✅ Passed |
| V-003 | Required field check | Leave tournament name empty | Error: “Tournament name is required.” | ✅ Passed |
| V-004 | Numeric field validation | Enter negative price in store | Error: “Price must be a positive number.” | ✅ Passed |
| V-005 | Missing mandatory data | Submit form with missing fields | Highlight missing fields | ✅ Passed |

---

### 4.2 API Testing

Responses include both *success* and *failure* cases.

---

#### 4.2.1 Login API

*Request*

```http
POST /api/login
Content-Type: application/json

{
  "email": "player1@chesshive.com",
  "password": "Password123"
}