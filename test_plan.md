# ChessHive – Test Plan

## 1. Overview

This document outlines the testing plan for the ChessHive Web Application, covering **Functional, **Validation, **UI, **Backend/API, and **Integration testing.  
It includes test cases, expected outputs, and sample API requests/responses for backend verification.

---

## 2. Testing Scope

- Functional Testing: Verify user functionalities for Coordinators, Organizers, Players, and Admins.  
- Validation Testing: Check input constraints and form data correctness.  
- UI Testing: Confirm responsive layout and dynamic UI elements.  
- API Testing: Validate backend routes, JSON responses, and HTTP status codes.  
- Integration Testing: Ensure seamless data flow between frontend and backend components.

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

All API tests are performed using Postman and MongoDB Compass.  
Responses include both success and failure cases.

---

#### 4.2.1 Player Profile API

Request

```http
GET /player/api/profile

{
  "player": {
    "AICF_ID": "987684oKLhn",
    "FIDE_ID": "80794erf9b",
    "college": "IIITS",
    "deletedAt": "2025-10-11T16:21:03.902Z",
    "dob": "2005-11-06T00:00:00.000Z",
    "draws": 22,
    "email": "teja@gmail.com",
    "gamesPlayed": 27,
    "gender": "female",
    "isDeleted": 0,
    "losses": 1,
    "name": "TEJA",
    "password": "Ppwd@123",
    "phone": "0086050301",
    "rating": 430,
    "restored_by": "admin@gmail.com",
    "restored_date": "2025-10-12T07:13:11.958Z",
    "role": "player",
    "sales": ["BOARD", "BOARD", "BOARD 34", "BOARD", "BOARD", "BOARD", "BOARD 34", "BOARD 34"],
    "subscription": {
      "_id": "68df80cfedfd6d12cf65b9d6",
      "username": "teja@gmail.com",
      "end_date": "2025-12-11T00:00:00.000Z"
    },
    "walletBalance": 69254,
    "winRate": 14.81,
    "wins": 4,
    "_id": "68c25d9da6ff9ccd7b7132e"
  },
  "subscribed": true
}

---

GET /coordinator/api/store/products

{
  "products": [
    { "_id": "68df7fc171dd7c13752bde40", "name": "BOARD", "price": 400, "image_url": "data:image/jpeg;base64,..." },
    { "_id": "68df7ffe971dd7c13752bde41", "name": "BOARD", "price": 400, "image_url": "data:image/png;base64,..." },
    { "_id": "68e53063ed9ffcb95c3b8202", "name": "chess queen piece", "category": "pieces", "price": 20 },
    { "_id": "68e533dfed9ffcb95c3b8023", "name": "chess queen piece", "category": "pieces", "price": 20 },
    { "_id": "68e9219a4f4b2119a2ef2473", "name": "BOARD", "category": "hehe", "price": 20, "image_url": "d" },
    { "_id": "68eb51ea12c617f69d5a4c9", "name": "kmjhgf", "category": "hehe", "price": 20, "image_url": "d" }
  ]
}

GET /organizer/api/coordinators

[
  { "_id": "68c25d9a6ff9ccd7b7123a", "name": "COORDINATORzero", "college": "IIIT HYd", "email": "coordinator0@gmail.com", "isDeleted": 0 },
  { "_id": "68c25d049a6ff9ccd7b7123b", "name": "COORDINATORone", "college": "IIIT HYd", "email": "coordinator1@gmail.com", "isDeleted": 1 },
  { "_id": "68c25d2b9a6ff9ccd7b7123c", "name": "COORDINATORtwo", "college": "IIITS", "email": "coordinator2@gmail.com", "isDeleted": 0 },
  { "_id": "68c25d629a6ff9ccd7b7123d", "name": "COORDINATORtHREE", "college": "IIITS", "email": "coordinator3@gmail.com", "isDeleted": 0 }
]

GET /admin/api/players

[
  { "_id": "68c25d9d9a6ff9ccd7b7123e", "name": "TEJA", "college": "IIITS", "email": "teja@gmail.com", "isDeleted": 0 },
  { "_id": "68c25dc29a6ff9ccd7b7123f", "name": "MOULYA", "college": "IIITS", "email": "moulya@gmail.com", "isDeleted": 0 },
  { "_id": "68c25df19a6ff9ccd7b71240", "name": "ASHU", "college": "IIITS", "email": "ashu@gmail.com", "isDeleted": 0 },
  { "_id": "68c25e1a9a6ff9ccd7b71241", "name": "VIVASH", "college": "IIITS", "email": "vivash@gmail.com", "isDeleted": 0 },
  { "_id": "68c25e429a6ff9ccd7b71242", "name": "NEELU KUAMR", "college": "IIITS", "email": "neelukumar@gmail.com", "isDeleted": 1 },
  { "_id": "68e15bbe277cc81e5b8a6f2b", "name": "nk", "college": "IIITS", "email": "nk@gmail.com", "isDeleted": 0 },
  { "_id": "68e1693e38a16fb01d1b69a3", "name": "v", "college": "IIITS", "email": "v@gmail.com", "isDeleted": 0 }
]


GET /coordinator/api/player-stats


{
  "players": [
    { "_id": "68e15c24df30ee25b5c7f427", "name": "nk", "rating": 630, "wins": 24, "losses": 1, "draws": 3, "gamesPlayed": 28 },
    { "_id": "68eb739188136b6c401a8c44", "name": "MOULYA", "rating": 520, "wins": 13, "losses": 1, "draws": 6, "gamesPlayed": 20 },
    { "_id": "68e15c24df30ee25b5c7f428", "name": "nk", "rating": 450, "wins": 17, "losses": 12, "draws": 0, "gamesPlayed": 29 },
    { "_id": "68eb73ec88136b6c401a8c45", "name": "ASHU", "rating": 440, "wins": 9, "losses": 5, "draws": 12, "gamesPlayed": 26 },
    { "_id": "68e72a16f2a4cae97165454d", "name": "TEJA", "rating": 430, "wins": 4, "losses": 1, "draws": 22, "gamesPlayed": 27 },
    { "_id": "68ea853b11abf1a29760950f", "name": "v", "rating": 410, "wins": 7, "losses": 6, "draws": 7, "gamesPlayed": 20 }
  ]
}