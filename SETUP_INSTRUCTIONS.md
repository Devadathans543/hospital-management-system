# Hospital Management System - DBMS Mini Project

## How to Implement This Code in VS Code

### Prerequisites
1. **Node.js** (v18 or higher) - Download from https://nodejs.org/
2. **VS Code** - Download from https://code.visualstudio.com/
3. **PostgreSQL Database** - You need a PostgreSQL database (Neon, Supabase, or local PostgreSQL)

### Step 1: Download the Project

**Option A: Using v0 CLI (Recommended)**
```bash
npx shadcn@latest add "https://v0.dev/chat/YOUR_CHAT_URL"
```

**Option B: Manual Download**
1. Click the three dots menu (⋮) in the top right of v0
2. Select "Download ZIP"
3. Extract the ZIP file to your desired location

### Step 2: Open in VS Code
```bash
cd hospital-management-system
code .
```

### Step 3: Install Dependencies
Open the integrated terminal in VS Code (Ctrl + ` or View > Terminal) and run:
```bash
npm install
# or
pnpm install
```

### Step 4: Set Up PostgreSQL Database

#### Option A: Using Neon (Recommended - Free)
1. Go to https://neon.tech and create a free account
2. Create a new project
3. Copy the connection string

#### Option B: Using Local PostgreSQL
1. Install PostgreSQL on your machine
2. Create a new database: `CREATE DATABASE hospital_management;`
3. Use connection string: `postgresql://username:password@localhost:5432/hospital_management`

### Step 5: Configure Environment Variables
1. Create a `.env.local` file in the root directory:
```env
DATABASE_URL=your_postgresql_connection_string_here
```

### Step 6: Run Database Migrations
Execute the SQL scripts in order:

**Using psql (command line):**
```bash
psql $DATABASE_URL -f scripts/001-create-tables.sql
psql $DATABASE_URL -f scripts/002-add-blood-group.sql
psql $DATABASE_URL -f scripts/003-clear-sample-data.sql
```

**Or using a GUI tool like pgAdmin or DBeaver:**
1. Connect to your database
2. Run each SQL file in the `scripts/` folder in order

### Step 7: Start the Development Server
```bash
npm run dev
# or
pnpm dev
```

### Step 8: Open in Browser
Navigate to http://localhost:3000

### Step 9: Register an Admin Account
1. Click "Register here" on the login page
2. Create your admin account
3. Login with your credentials

---

## Project Structure

```
hospital-management-system/
├── app/
│   ├── api/                    # Backend API Routes
│   │   ├── auth/               # Authentication APIs
│   │   │   ├── login/
│   │   │   ├── logout/
│   │   │   ├── register/
│   │   │   └── session/
│   │   ├── doctors/
│   │   ├── patients/
│   │   ├── appointments/
│   │   ├── medical-records/
│   │   ├── billing/
│   │   └── stats/
│   ├── login/                  # Login Page
│   ├── register/               # Registration Page
│   ├── patients/               # Patients Management
│   ├── doctors/                # Doctors Management
│   ├── appointments/           # Appointments Management
│   ├── medical-records/        # Medical Records
│   ├── billing/                # Billing Management
│   ├── layout.tsx              # Root Layout
│   ├── page.tsx                # Dashboard (Home)
│   └── globals.css             # Global Styles
├── components/
│   ├── ui/                     # Shadcn UI Components
│   ├── auth-provider.tsx       # Authentication Context
│   ├── data-table.tsx          # Reusable Data Table
│   ├── navbar.tsx              # Navigation Bar
│   └── protected-layout.tsx    # Protected Route Wrapper
├── lib/
│   ├── auth.ts                 # Authentication Utilities
│   ├── db.ts                   # Database Connection & Types
│   └── utils.ts                # Utility Functions
├── scripts/                    # SQL Migration Scripts
│   ├── 001-create-tables.sql
│   ├── 002-add-blood-group.sql
│   └── 003-clear-sample-data.sql
└── package.json
```

---

## Database Schema (ER Diagram)

```
┌──────────────────┐       ┌──────────────────┐
│     DOCTORS      │       │     PATIENTS     │
├──────────────────┤       ├──────────────────┤
│ doctor_id (PK)   │       │ patient_id (PK)  │
│ first_name       │       │ first_name       │
│ last_name        │       │ last_name        │
│ specialization   │       │ date_of_birth    │
│ phone            │       │ gender           │
│ email            │       │ phone            │
│ department       │       │ email            │
│ created_at       │       │ address          │
└────────┬─────────┘       │ blood_group      │
         │                 │ created_at       │
         │                 └────────┬─────────┘
         │                          │
         │    ┌─────────────────────┼─────────────────────┐
         │    │                     │                     │
         ▼    ▼                     ▼                     ▼
┌──────────────────┐       ┌──────────────────┐  ┌──────────────────┐
│   APPOINTMENTS   │       │ MEDICAL_RECORDS  │  │     BILLING      │
├──────────────────┤       ├──────────────────┤  ├──────────────────┤
│ appointment_id   │       │ record_id (PK)   │  │ bill_id (PK)     │
│ patient_id (FK)  │◄──────│ patient_id (FK)  │  │ patient_id (FK)  │
│ doctor_id (FK)   │       │ doctor_id (FK)   │  │ appointment_id   │
│ appointment_date │       │ diagnosis        │  │ amount           │
│ appointment_time │       │ treatment        │  │ payment_status   │
│ status           │       │ prescription     │  │ payment_method   │
│ reason           │       │ visit_date       │  │ bill_date        │
│ created_at       │       │ created_at       │  │ created_at       │
└──────────────────┘       └──────────────────┘  └──────────────────┘
```

---

## Key Features

### 1. Admin Authentication
- Secure login/registration system
- Session-based authentication with cookies
- SHA-256 password hashing

### 2. CRUD Operations
- **Create**: Add new patients, doctors, appointments, records, and bills
- **Read**: View all records in searchable tables
- **Update**: Edit existing records
- **Delete**: Remove records from the database

### 3. Relational Database Features
- **Foreign Keys**: Appointments link to both patients and doctors
- **JOIN Queries**: Display patient/doctor names in related tables
- **Referential Integrity**: Database enforces relationships

### 4. Billing in Indian Rupees (₹)
- All amounts displayed in INR format
- Supports multiple payment methods
- Payment status tracking (Pending, Paid, Cancelled, Refunded)

---

## Technologies Used

| Layer      | Technology                    |
|------------|-------------------------------|
| Frontend   | Next.js 14, React, TypeScript |
| Styling    | Tailwind CSS, Shadcn/UI       |
| Backend    | Next.js API Routes (Node.js)  |
| Database   | PostgreSQL (Neon)             |
| Auth       | Custom session-based auth     |

---

## Troubleshooting

### "Cannot connect to database"
- Check your DATABASE_URL in `.env.local`
- Ensure the database is running and accessible
- Try running: `psql $DATABASE_URL` to test connection

### "Module not found" errors
- Run `npm install` again
- Delete `node_modules` and `.next` folders, then reinstall

### "Port 3000 already in use"
- Kill the existing process: `npx kill-port 3000`
- Or use a different port: `npm run dev -- -p 3001`

---

## For DBMS Project Submission

This project demonstrates:
1. **Relational Database Design** - 5 interconnected tables
2. **SQL Operations** - INSERT, SELECT, UPDATE, DELETE with JOINs
3. **Foreign Key Relationships** - Proper referential integrity
4. **Full-Stack Implementation** - Frontend + Backend + Database
5. **CRUD Operations** - Complete data management capabilities

Good luck with your DBMS mini project!
