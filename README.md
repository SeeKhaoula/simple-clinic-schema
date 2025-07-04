# 🏥 Simple Clinic – Relational Schema

## 📌 Project Requirements

### Project 1 – Simple Clinic (Requirements)

Create Relational Schema for the following project:

#### 1. Patients:
- The database should store information about patients.
- Each patient should have a unique identifier, a name, a date of birth, gender, contact information (phone number, email), and address.

#### 2. Doctors:
- The database should store information about doctors.
- Each doctor should have a unique identifier, a name, specialization, a date of birth, gender, contact information (phone number, email), and address.

#### 3. Appointments:
- The database should store information about appointments.
- Each appointment should have a unique identifier, a patient, a doctor, appointment date and time, and appointment status.
- Appointment Status:
  - Pending: The appointment has been scheduled but has not yet occurred.
  - Confirmed: The appointment has been confirmed by both the patient and the healthcare provider.
  - Completed: The appointment has taken place as scheduled.
  - Canceled: The appointment has been canceled either by the patient or the healthcare provider.
  - Rescheduled: The appointment has been rescheduled for a different date or time.
  - No Show: The patient did not show up for the appointment without canceling or rescheduling.

#### 4. Medical Records:
- The database should store medical records for patients.
- For each attended appointment there should be a medical record.
- Each medical record should have a unique identifier, a patient, a doctor, a description of the visit, diagnosis, prescribed medication, and any additional notes.

#### 5. Prescription:
- The database should store information about prescribed medications.
- For each medical record there should be at most one prescription.
- Each prescription should have a unique identifier, a medical record, medication name, dosage, frequency, start date, end date, and any special instructions.

#### 6. Payments:
- The database should store information about payments.
- Payment is per appointment.
- Each payment should have a unique identifier, a patient, a payment date, payment method, amount paid, and any additional notes.


## 📊 My Relational Schema Design

To design the database, I followed normalization principles and separated the information into logical tables to reduce redundancy and represent real-world relationships clearly.

### 1. Persons Table  
Since both `Patients` and `Doctors` share personal details like name, birth date, gender, phone, email, and address, I created a single `Persons` table that stores all personal data.

### 2. Patients & Doctors  
- `Patients(PatientID, PersonID)`  
- `Doctors(DoctorID, PersonID, Specialization)`  
Both reference the `Persons` table to avoid repeating personal data.

### 3. Appointments  
Stores the appointment information and connects patients with doctors. Includes date/time and a status field with allowed values (Pending, Confirmed, etc.).

### 4. MedicalRecords
Every attended appointment generates a medical record that includes description, diagnosis, medication, and notes. It has a one-to-one relationship with appointments.

### 5. Prescriptions 
Each medical record can have at most one prescription. It includes medication details like name, dosage, start/end date, and instructions.

### 6. Payments  
Each appointment must have a payment associated with it. The table stores the amount, date, payment method, and references both the patient and appointment.


## 🔗 Relationships Between Tables

| From Table       | To Table         | Type of Relationship     |
|------------------|------------------|---------------------------|
| Patients         | Appointments     | One-to-Many               |
| Doctors          | Appointments     | One-to-Many               |
| Appointments     | MedicalRecords   | One-to-One                |
| MedicalRecords   | Prescriptions    | One-to-One                |
| Appointments     | Payments         | One-to-One                |
| Patients         | Payments         | One-to-Many               |


This schema ensures high normalization, reflects real-world relations, and is ready for SQL implementation and GitHub documentation.

