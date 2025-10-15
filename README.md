# MSK Backend — .NET 8 Minimal API

A clean, production-shaped **.NET 8** backend that powers the MSK Suggestions UI. It’s intentionally simple but professional: **minimal APIs**, **repository pattern**, **EF Core (InMemory by default)**, and **DTOs that match the Angular app** (string enums, ISO dates). Turn it on and the frontend feels like a real system—no template changes required.

---

## Highlights

* **Modern .NET 8 stack** (Minimal APIs, EF Core, AutoMapper).
* **Clean layers**: Domain (entities), Application (DTOs/contracts), Infrastructure (DbContext/repos), Api (endpoints, DI, CORS).
* **Frontend-friendly shapes**: status/type/priority as strings, ISO timestamps.
* **Dev-ready**: InMemory DB + seed data; Swagger; CORS for `http://localhost:4200`.

---

## Quick Start

```bash
dotnet restore
dotnet run --project Msk.Api
```

* Swagger: shown in console (e.g., `http://localhost:5xxx/swagger`).

**Hook up Angular**: set `environment.apiBase = 'http://localhost:5xxx/api'`.

> If you see browser blocks, keep both app and API on **http** during dev, or enable HTTPS + proper CORS origins.

---

## Key Endpoints (base `/api`)

* `GET /employees`
* `GET /suggestions` · `POST /suggestions` · `PATCH /suggestions/{id}` · `DELETE /suggestions/{id}`
* `GET /suggestions/{id}/comments` · `POST /suggestions/{id}/comments`

---

## Data Model (brief)

* **Employee**: Id, Name, Email, Department, RiskLevel?
* **Suggestion**: Id, EmployeeId, Type, Priority, Status, Source, DateCreated/Updated, DateCompleted?, Description, Notes?
* **Comment**: Id, SuggestionId, Author, Text, Date
  Enums as strings: `pending|in_progress|completed|dismissed|overdue`, `low|medium|high`, `exercise|equipment|behavioural|lifestyle`.

---

## Optional: Switch to SQL later

Replace InMemory with SQL Server in DI and add a connection string—no API/Angular changes needed.

---

## License

Internal demo project (no license specified). Use and adapt freely.
