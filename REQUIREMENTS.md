# MEDLINK – Unified Medical Database

### Assignment 3: Requirements Engineering and Specification

**Group:** G_09  

---

## 👥 Members & Roles
| Member | Role | Description |
|---------|------|-------------|
| **Mohammed Shazad** | Requirements Elicitation Lead & Coordinator | Conducts elicitation through brainstorming, interviews, and online research. |
| **Maad Kamal** | Requirements Specification Specialist & Priority Analyst | Classifies and prioritizes requirements (M/N/S) and organizes user vs system requirements. |
| **Zaid Omer** | Use Case Modeler | Specifies actors and creates UML diagrams for visualization. |
| **Mahmood Abdulasalam** | Structured Specification Developer & Validation Lead | Develops structured requirement specifications and handles validation. |

---

## 🏥 Project Overview
MedLink is a centralized healthcare data system that unifies patient medical information across hospitals, clinics, and laboratories. The platform allows authorized doctors and healthcare administrators to access, update, and share medical records securely through encrypted channels, improving care coordination and data integrity nationwide.

---

## 1️⃣ Requirements Elicitation (Mohammed Shazad)

**Techniques Used:**
- **Brainstorming:** Team sessions to outline core requirements for medical record accessibility.  
- **Interviews:** Conducted with qualified medical professionals to gather insight into essential features.  
- **Online Research:** Reviewed existing healthcare systems such as:  
  - [The Importance of Unified Medical Records](https://www.nvssoft.com/insight_post/the-importance-of-unified-medical-records/)  
  - [Saudi Ministry of Health – Unified Health File](https://www.moh.gov.sa/en/Ministry/Unified-Health-File/Pages/default.aspx)

**Overview of Requirements:**
- Doctors can view patient history across hospitals and update diagnoses or prescriptions.  
- Authorized staff can add or modify records.  
- Patients can register, view, and manage limited personal data (cannot alter doctor inputs).  
- Patient consent is mandatory for access.  
- Hospitals can integrate via API.  
- Must be available on both web and mobile platforms.  
- Query response time < 2 seconds.  
- System must comply with privacy and data protection laws.  
- Ministry of Health can monitor national-level health data.  
- Lab technicians can upload and verify test results.

---

## 2️⃣ Requirement Specifications (Maad Kamal)

### **Overview**
Elicited requirements were analyzed and categorized into:  
1. **Functional vs. Non-Functional:** Defines what the system does vs. how it performs.  
2. **User vs. System:** Defines who interacts with or enforces each requirement.

### **A. Functional vs. Non-Functional Requirements**
| ID | Requirement Description | Type |
|----|--------------------------|------|
| R1 | Doctor can search for patient by National ID | Functional |
| R2 | Hospitals can upload medical reports | Functional |
| R3 | Patients can view their own medical records | Functional |
| R4 | All communication must be encrypted via HTTPS/TLS | Non-Functional |
| R5 | System must use Role-Based Access Control (RBAC) | Functional |
| R6 | Interface must support Arabic and English | Non-Functional |
| R7 | Database should allow real-time data retrieval | Non-Functional |
| R8 | Ministry can generate national health reports | Functional |
| R9 | System must log all data access and modification | Functional |
| R10 | System should maintain at least 99% uptime | Non-Functional |

### **B. User vs. System Requirements**
| ID | Requirement Description | Type |
|----|--------------------------|------|
| R1 | Doctor can search for patient by National ID | User |
| R2 | Hospitals can upload medical reports | User |
| R3 | Patients can view their medical records | User |
| R4 | Data encrypted via HTTPS/TLS | System |
| R5 | Implement RBAC for data access | System |
| R6 | Multilingual interface (Arabic/English) | System |
| R7 | Real-time data retrieval and performance | System |
| R8 | Ministry can generate national reports | User |
| R9 | All actions logged for auditing | System |
| R10 | Maintain 99% uptime | System |
| R11 | Doctor collaboration platform | User |

---

## 3️⃣ Structured Specification (Mahmood Abdulasalam)

### **Overview**
This section specifies three critical functional requirements of the MedLink system, describing their purpose, inputs, outputs, and interactions with the system.

#### **Function: User Authentication and Access Control**
**Related Requirements:** R5 (RBAC), R4 (Encryption), R9 (Logging)  

Authenticates doctors, administrators, and hospital staff before granting access. Only authorized users can view or modify patient data using encrypted sessions.

**Inputs:**  
- National ID (verified unique identifier)  
- Password (hashed in database)  
- Role type (Doctor/Admin)

**Outputs:**  
- Authentication token (JWT)  
- Success/error message  
- Redirect to dashboard

**Actions:**  
- Verify National ID and password against stored credentials.  
- On success, generate JWT and session.  
- On failure, log attempt and deny access.  

**Side Effects:**  
- Session timeout after 15 min of inactivity.  
- Lockout after repeated failed attempts.

---

#### **Function: Patient Record Management**
**Related Requirements:** R1, R2, R3, R9  

Allows authenticated doctors to create, read, and update patient medical records securely.

**Inputs:**  
- Patient ID, Doctor ID  
- Medical details (diagnosis, prescriptions, lab results)

**Outputs:**  
- Updated or retrieved record  
- Validation or error message  

**Actions:**  
- Validate authorization and perform CRUD operations.  
- Timestamp each update and log the doctor ID.  

**Side Effects:**  
- Syncs updates with backup database.

---

#### **Function: Inter-Hospital Data Sharing**
**Related Requirements:** R6, R4, R9  

Allows hospitals in the MedLink network to exchange patient records securely through encrypted APIs.

**Inputs:**  
- Hospital ID  
- Patient UUID  
- Authorization token  

**Outputs:**  
- Encrypted patient data or error message  

**Actions:**  
- Validate hospital identity and access permissions.  
- Encrypt data and transmit via HTTPS.  

**Side Effects:**  
- May increase bandwidth load during heavy use.

---

## 4️⃣ Requirements Prioritization (Maad Kamal)
| ID | Description | Priority | Justification |
|----|--------------|-----------|----------------|
| R1 | Doctor search by National ID | M | Core functionality |
| R2 | Upload medical reports | M | Enables record creation |
| R3 | Patient access to medical records | M | Increases transparency |
| R4 | Encrypted communication | M | Legal and security requirement |
| R5 | Role-Based Access Control | M | Ensures privacy and authorization |
| R6 | Multilingual interface | N | Adds accessibility |
| R7 | Real-time data retrieval | N | Enhances performance |
| R8 | National health reports | N | Government-level analytics |
| R9 | Audit logging | M | Compliance and traceability |
| R10 | 99% uptime | M | Ensures system reliability |
| R11 | Doctor collaboration feature | S | Optional for future expansion |

**Legend:**  
*M – Mandatory | N – Nice to Have | S – Superfluous*

---

## 5️⃣ Primary Actors and Descriptions (Zaid Omer)

| Actor | Description |
|-------|--------------|
| **Patient** | Registers on the platform, views and updates personal information, and accesses medical records and lab results. |
| **Doctor** | Accesses patient medical data, updates diagnoses and prescriptions, and reviews lab results. |
| **Hospital/Clinic Administrator** | Manages hospital user accounts, approves or revokes access, and generates reports. |
| **Laboratory Technician** | Uploads, updates, and verifies patient test results. |
| **Ministry of Health (MOH)** | Monitors national healthcare data, accesses reports, and oversees compliance. |
| **System Administrator** | Maintains security, user permissions, and system performance. |

---

## ✅ Conclusion
The MedLink system delivers a unified, secure, and efficient healthcare data platform that connects hospitals, doctors, and patients nationwide. By applying structured requirements engineering, the project ensures data integrity, privacy, and accessibility—paving the way for a more connected and transparent healthcare ecosystem.
