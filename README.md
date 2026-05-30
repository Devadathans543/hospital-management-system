# hospital-management-system
A comprehensive web-based application engineered to transform traditional hospital operations through complete automation and digital integration.
# Hospital Management System (HMS)

A web-based **Hospital Management System (HMS)** designed to automate and streamline basic hospital operations such as patient management, appointment scheduling, doctor details, medical reports, and billing.

## Project Overview

This project is developed as part of the **Database Systems (PBCMT404)** course at **Sree Chitra Thirunal College of Engineering, Department of CSE (AI & ML)**. The system provides a centralized platform for managing hospital workflows with role-based access for different users.

## Institution

- **College:** Sree Chitra Thirunal College of Engineering
- **Department:** CSE AI & ML
- **Course:** Database Systems (PBCMT404)
- **Instructor:** Surekha I S

## Features

- Patient registration and management
- Appointment booking and scheduling
- Doctor details and availability management
- Medical report handling
- Billing and payment tracking
- Role-based access for:
  - Admin
  - Doctor
  - Receptionist
  - Patient
- Search and retrieval of patient records
- Responsive web interface

## System Modules

### 1. Patient Management
Handles patient registration, profile details, medical history, and emergency information.

### 2. Appointment Scheduling
Allows patients or receptionists to book appointments based on doctor availability.

### 3. Medical Report Handling
Stores and retrieves electronic medical records securely.

### 4. Billing and Payments
Supports invoice generation, payment status tracking, and service-wise billing.

## Technology Stack

- **Frontend:** HTML, CSS, JavaScript
- **Backend:** Django / Python
- **Database:** PostgreSQL / SQLite
- **Version Control:** Git & GitHub

## Installation

1. Clone the repository:
```bash
git clone https://github.com/your-username/your-repo-name.git
cd your-repo-name
```

2. Create a virtual environment:
```bash
python -m venv venv
```

3. Activate the virtual environment:

- Windows:
```bash
venv\Scripts\activate
```

- macOS/Linux:
```bash
source venv/bin/activate
```

4. Install dependencies:
```bash
pip install -r requirements.txt
```

If `requirements.txt` is not available, install Django manually:

```bash
pip install django
```

5. Run migrations:
```bash
python manage.py makemigrations
python manage.py migrate
```

6. Create a superuser:
```bash
python manage.py createsuperuser
```

7. Run the server:
```bash
python manage.py runserver
```

## Working Steps

1. Open the application in your browser at:
```bash
http://127.0.0.1:8000/
```

2. Log in with your credentials.

3. Use the dashboard to manage:
- Patients
- Doctors
- Appointments
- Medical records
- Billing

4. For admin access, go to:
```bash
http://127.0.0.1:8000/admin/
```

## System Architecture

The application follows a role-based web architecture with separate access levels for:

- **Admin:** Full control over the system
- **Doctor:** Access to patient records and consultation-related data
- **Receptionist:** Manages appointments, check-ins, and billing
- **Patient:** Views personal records and appointment details

## Project Highlights

- Centralized hospital data management
- Secure and role-based access control
- Improved efficiency in hospital workflow
- Reduced manual errors in appointment and record handling
- Responsive and user-friendly interface

## Future Enhancements

- Mobile application support
- Online payment gateway integration
- SMS or WhatsApp appointment reminders
- AI-based doctor/patient assistance
- Laboratory and pharmacy module integration
- Telemedicine support

## Conclusion

The Hospital Management System provides an efficient digital solution for managing core hospital operations. It reduces manual workload, improves data accuracy, and supports better coordination between hospital staff and patients.

## Authors

- **Devadathan S**

## License

This project is intended for academic purposes.
