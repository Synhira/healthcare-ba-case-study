# HealthTech Business Analysis Case Study: Patient Online Booking Integration

## 📌 Context & Objective
**Goal:** Enable patients to book medical appointments online via the website directly into the Healthcare Information System (MIS) to reduce call-center workload, prevent double-booking, and improve patient experience.

---

## 📐 Business Process Specification (BPMN Flow)

### Process Steps:
1. **Patient** selects Specialty, Doctor, Location, and Time Slot on the website.
2. **Website** calls MIS API to verify slot availability.
3. **Patient** submits personal details (First Name, Last Name, Phone Number, DOB).
4. **MIS** validates patient data:
   - Matches Phone + DOB to prevent duplicate patient profiles.
   - Links booking to existing profile OR creates a new draft profile.
5. **MIS** updates slot status to "Booked" and sends confirmation.
6. **Patient** receives automated confirmation message (Viber/SMS via TurboSMS API).

---

## 📝 User Stories & Acceptance Criteria (Jira / Backlog)

### **US-01: View Available Slots for Online Booking**
**As a** Patient,  
**I want to** see real-time doctor availability on the website,  
**So that** I can select a convenient date and time for my appointment.

#### **Acceptance Criteria (AC):**
* **AC 1:** The system displays available time slots based on the doctor's active schedule in the MIS.
* **AC 2:** Past slots and already booked slots are hidden or disabled.
* **AC 3:** Time slots update automatically upon page refresh.

---

### **US-02: Patient Online Appointment Booking**
**As a** Patient,  
**I want to** book an appointment by filling in my basic contact info,  
**So that** my appointment is registered instantly without calling the reception.

#### **Acceptance Criteria (AC):**
* **AC 1:** Mandatory fields: First Name, Last Name, Phone Number (+380 format), Date of Birth.
* **AC 2:** Upon submission, the MIS checks if the slot is still available.
* **AC 3:** If available, status `201 Created` is returned, slot status changes to "Booked" in MIS schedule, and appointment appears on the doctor's calendar.
* **AC 4 (Error Handling):** If slot was taken concurrently by another user, return error `409 Conflict`: *"The selected slot is no longer available. Please choose another time."*

---

## 🖥️ Low-Fidelity UI Wireframe (Wireframe Concept)

### **Appointment Confirmation Form (Website)**
