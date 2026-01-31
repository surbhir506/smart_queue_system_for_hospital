1️⃣ Problem Statement

In hospitals, patients often face long and unpredictable waiting times even after booking appointments. Delays caused by emergencies, extended consultations, or staff unavailability lead to overcrowding, frustration, and inefficient use of hospital resources. Patients lack real-time visibility into queue status, while hospital staff do not have intelligent tools to dynamically redistribute appointments and balance service load. This system aims to provide a secure, real-time, and adaptive appointment and queue management platform to reduce waiting time, improve patient experience, and optimize hospital operations.

2️⃣ User Roles (Hospital Specific)

The system supports the following user roles:

### 3.1 Patient
- Register and log in securely
- Book appointments
- View appointment and queue status
- Receive notifications for delays or rescheduling

### 3.2 Doctor
- View assigned appointments and queues
- Update patient status (In Consultation, Completed)
- Mark no-shows

### 3.3 Receptionist (Staff)
- Manage appointment slots
- Handle walk-ins
- Detect and manage delays
- Assist patients with rescheduling

### 3.4 Admin
- Manage users and roles
- Configure departments and doctors
- View analytics and reports
- Monitor system health

---

3️⃣ Core Functional Features 

🔐 A. Authentication & Security

Patient / Doctor / Staff / Admin login

JWT-based authentication

Refresh token handling

Role-based access control

Secure logout

📅 B. Appointment Management

Department-wise booking (e.g., Cardiology, OPD)

Doctor availability slots

Slot capacity enforcement

Waitlist when slots are full

Appointment cancel & reschedule

📌 Real-world rule:

A doctor can handle only N patients per slot.

⏳ C. Smart Queue Management

Automatic queue creation per doctor

FIFO queue ordering

Priority handling (emergency patients)

Queue states:

Waiting

In Queue

In Consultation

Completed

No-show / Skipped

Real-time queue position for patients

⚖️ D. Load Balancing Logic (Key Feature)

Detect doctor delay (late start / long consultation)

Auto-shift patients to:

Next available slot

Another doctor in same department

Update queue dynamically

Notify affected patients

📌 This is what makes your project non-trivial.

📊 E. Hospital Admin Dashboard

Daily appointment count

Average waiting time per doctor

Peak hours

Missed / no-show appointments

Department-wise load

4️⃣ Workflow Definitions 

🧭 Appointment Booking Flow
Patient → Select Department → Select Doctor → Select Slot
        → Slot Available?
            ├─ Yes → Appointment Confirmed
            └─ No  → Added to Waitlist

🧭 Queue Flow (Doctor Side)
Waiting → In Queue → In Consultation → Completed
                     ↓
                  No-show → Skipped

🧭 Delay & Load Balancing Flow
Delay Detected
   ↓
Recalculate Queue
   ↓
Reschedule / Reassign
   ↓
Notify Patients


📌 These flows will directly become backend logic later.

5️⃣ Non-Functional Requirements

🔒 Security

JWT + Refresh Tokens

Role-based API protection

No sensitive data in logs

HTTPS enforced

⚡ Performance

Fast queue position lookup

Handle concurrent bookings

Optimized DB queries

📈 Scalability

Stateless backend APIs

Easily extensible to SignalR

Future Redis caching support

🛡 Reliability

Global exception handling

Audit logs for critical actions

Transaction safety for bookings
