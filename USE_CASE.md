# Use Case Diagram Documentation – MedLink System

---

## 1. System Overview
The MedLink system is a nationwide healthcare platform designed to unify hospital and clinical databases across Iraq.  
It enables secure access, management, and sharing of patient medical data between hospitals, laboratories, and the Ministry of Health.  
The platform replaces fragmented paper-based systems with a centralized, digital solution, improving accuracy, accessibility, and efficiency in healthcare services.

---

## 2. System Scope
The MedLink system connects multiple stakeholders in healthcare — patients, doctors, hospital administrators, laboratory technicians, the Ministry of Health, and system administrators — under one digital infrastructure.  
It supports centralized medical record storage, secure user authentication and access control, data management and reporting functionalities, and nationwide health monitoring by the Ministry of Health.

---

## 3. Primary Actors and Descriptions

| Actor | Description |
|-------|--------------|
| **Patient** | Registers on the platform, views and updates personal information, and accesses medical records and lab results. |
| **Doctor** | Accesses patient medical data, updates diagnoses and prescriptions, and reviews lab results. |
| **Hospital/Clinic Administrator** | Manages hospital user accounts, approves or revokes access, and generates reports. |
| **Laboratory Technician** | Uploads, updates, and verifies patient test results. |
| **Ministry of Health (MOH)** | Monitors national healthcare data, accesses reports, and oversees compliance. |
| **System Administrator** | Maintains security, user permissions, and overall system performance. |

---

## 4. Main Use Cases

### Patient
- Registers on the MedLink platform  
- Views and updates personal health information  
- Views medical history, prescriptions, and lab results  

### Doctor
- Logs into the system (authenticated user)  
- Searches and accesses patient medical records  
- Adds or updates diagnoses, prescriptions, and treatment notes  
- Requests and reviews lab results  

### Hospital/Clinic Administrator
- Manages hospital staff and system accounts  
- Approves or revokes doctor access  
- Generates hospital-level reports  

### Laboratory Technician
- Uploads and verifies patient test results  
- Updates laboratory data for patients  

### Ministry of Health (MOH)
- Monitors nationwide healthcare data  
- Accesses anonymized reports and statistics  
- Oversees compliance and data standards  

### System Administrator
- Manages user roles and access permissions  
- Ensures data security and system maintenance  
- Monitors system logs and performance  

---

## 5. Relationships Between Actors and Use Cases
All actors interact with the MedLink system according to their roles and permissions.  
Patients, doctors, laboratory technicians, and administrators directly use the system’s web interface.  
The Ministry of Health accesses aggregated and anonymized data for analysis, while the System Administrator ensures data integrity and security.

---

## 6. System Boundary
All identified use cases occur within the MedLink system boundary.  
External entities (actors) interact through defined interfaces such as dashboards or portals, while internal system processes manage authentication, data flow, and storage.

---

## 7. Summary
The MedLink Use Case Diagram defines a role-based healthcare management system that centralizes patient data across institutions.  
It ensures improved data accessibility, reduced redundancy, and better collaboration across Iraq’s healthcare network.
