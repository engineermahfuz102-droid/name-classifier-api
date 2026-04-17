# HNG12 Stage 1 - Data Persistence & API Design

This is a Backend API built for the HNG12 Internship Stage 1 task. It integrates with external APIs (Genderize, Agify, and Nationalize) to classify names and store the results in a persistent database.

## Features
- **Data Persistence:** Uses PostgreSQL with SQLAlchemy for robust data storage.
- **Multi-API Integration:** Fetches gender, age, and nationality data concurrently using `httpx` and `asyncio`.
- **Idempotency:** Prevents duplicate record creation for the same name.
- **Case-Insensitive Filtering:** Supports filtering profiles by gender, country, and age group regardless of casing.
- **UUID v7:** Uses time-ordered UUIDs for primary keys.
- **CORS Enabled:** Fully accessible by the HNG grading scripts.

## Tech Stack
- **Language:** Python 3.14+
- **Framework:** FastAPI
- **Database:** PostgreSQL (Production) / SQLite (Local Testing)
- **Asynchronous I/O:** httpx & asyncio

## API Endpoints

### 1. Create Profile
`POST /api/profiles`
- Body: `{ "name": "ella" }`
- Returns 201 Created or 200 OK (if exists).

### 2. Get All Profiles
`GET /api/profiles`
- Query Params: `gender`, `country_id`, `age_group` (all case-insensitive).

### 3. Get Single Profile
`GET /api/profiles/{id}`

### 4. Delete Profile
`DELETE /api/profiles/{id}`
- Returns 204 No Content.

## Local Setup

1. Clone the repository:
   ```bash
   git clone <your-repo-url>
   cd task-2