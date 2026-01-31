# Smart Queue & Appointment Load Balancer (Hospital)

## 1. Project Overview

Hospitals often struggle with long and unpredictable patient waiting times despite having appointment systems in place. Delays caused by emergencies, extended consultations, or staff unavailability result in overcrowding, poor patient experience, and inefficient resource utilization.

This project aims to build a **secure, intelligent, and scalable Smart Queue & Appointment Load Balancer** for hospitals. The system will provide real-time queue visibility to patients and enable hospital staff to dynamically manage appointments, queues, and service loads.

---

## 2. Problem Statement

In hospital environments, patients frequently experience long waiting periods even after booking appointments. Existing systems lack real-time queue tracking, intelligent delay handling, and load redistribution mechanisms. Hospital staff also lack tools to proactively manage appointment overruns and balance patient load across doctors or time slots.

This system addresses these challenges by providing:
- Real-time queue tracking
- Intelligent appointment load balancing
- Secure, role-based access
- Actionable analytics for hospital administration

---

## 3. User Roles

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

## 4. Functional Requirements

### 4.1 Authentication & Authorization
- Secure login and registration
- JWT-based authentication
- Refresh token mechanism
- Role-based authorization
- Secure logout

---

### 4.2 Appointment Management
- Department-wise appointment booking
- Doctor availability and slot management
- Slot capacity enforcement
- Waitlist handling for full slots
- Appointment cancellation and rescheduling

---

### 4.3 Smart Queue Management
- Automatic queue generation per doctor
- FIFO (First-In-First-Out) queue handling
- Priority handling for emergency cases
- Queue states:
  - Waiting
  - In Queue
  - In Consultation
  - Completed
  - No-show / Skipped
- Real-time queue position visibility for patients

---

### 4.4 Load Balancing & Delay Handling
- Detection of doctor delays
- Automatic rescheduling of affected appointments
- Reassignment to alternate doctors within the same department
- Dynamic queue recalculation
- Patient notifications for any changes

---

### 4.5 Admin Dashboard & Analytics
- Daily appointment volume
- Average waiting time per doctor
- Peak hours analysis
- No-show statistics
- Department-wise load distribution

---

## 5. System Workflows

### 5.1 Appointment Booking Workflow
Patient → Select Department → Select Doctor → Select Time Slot
→ Slot Available?
├─ Yes → Appointment Confirmed
└─ No → Added to Waitlist


---

### 5.2 Queue Management Workflow
Waiting → In Queue → In Consultation → Completed
↓
No-show → Skipped


---

### 5.3 Delay & Load Balancing Workflow
Delay Detected
↓
Recalculate Queue
↓
Reschedule or Reassign Appointment
↓
Notify Patient


---

## 6. Non-Functional Requirements

### 6.1 Security
- JWT and refresh token-based authentication
- Role-based API protection
- Secure password hashing
- No sensitive data exposure in logs
- HTTPS enforcement

---

### 6.2 Performance
- Efficient queue position lookup
- Support for concurrent appointment bookings
- Optimized database queries

---

### 6.3 Scalability
- Stateless backend APIs
- Ready for future real-time updates (SignalR)
- Extensible architecture for caching and scaling

---

### 6.4 Reliability
- Global exception handling
- Audit logs for critical actions
- Transaction safety during appointment booking

---

## 7. Success Criteria

The project will be considered successful if:
- Patients can clearly see queue positions and delays
- Appointment overruns are handled automatically
- Hospital staff can manage load effectively
- The system is secure, scalable, and maintainable
- The project can be confidently explained in technical interviews

---

## 8. Future Enhancements (Out of Scope for Now)
- SMS / Email notifications
- Mobile application
- Integration with hospital EMR systems
- AI-based delay prediction
