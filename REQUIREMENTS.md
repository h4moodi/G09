*MEDLINK our unified medical Database*


Our 3rd assignment is requirement engineering and specifications 


Group: G_09
Members & Roles 
       |
       V

       *Mohammed Shazad : Requirements Elicitations lead and Coordinator (Conducts Elicitation through several ways mainly through brainstorming and research)
       *Maad Kamal : Requirements specifications specialist and priority analyst (Classifies functional vs. non-functional requirements, organizes user vs. system requirements, and prioritizes them (M/N/S))
       *Zaid Omer Use Case Modeler : Specifies the actors and creates UML diagrams for visual purposes
       *Mahmood Abdulasalam : Structured Specification developer and validation lead 

Project overview
***************************************************
***************************************************


1- Requirements Elicitations(Mohammed Shazad){
    The techniques used for gathering requirements for story points and creating a platform to create our whole system off of are ways such as: 
    -brainstorming: Group sessions to layout basic needs for a doctor to know about a patient 
    -interviews:interviews done with some qualified indiviuals in the medical field to get ascope of whats needed
    -online research:several articles found throughout the internet such as   -https://www.nvssoft.com/insight_post/the-importance-of-unified-medical-records/
                                                                              -https://www.moh.gov.sa/en/Ministry/Unified-Health-File/Pages/default.aspx
}{
***Overview of The requirements***    
** Doctors should be able to view patient history across hospitals.
   -They should also be able to add or update diagnoses, prescriptions, and treatment notes
** System should support adding new records by authorized staff.
   -The hospital administrator should be able to manage the staff who can access the data and the queries done through the web interface  
** Patient consent should be required before data access.  
   -they should be able to register on the medlink platform
   -view and update personal information
   -view history of their visits to the doctor
   -PATIENTS CANNOT CHANGE ANY INFO THAT THE DOCTOR HAS SET FOR THEM 
** Hospitals can integrate via API.  
** Must be accessible through both web and mobile.  
** Response time < 2 seconds for standard queries.  
** Data must comply with healthcare privacy laws.
** Ministry of Health staff can monitor the nationwide data
** Labratory technicians can upload lab test.
}


2- Requirement Specifications (Maad Kamal): 


***Overview***
elicited requirements were analyzed and categorized into two parts:
1.Functional vs. Non-Functional – defines what the system does vs.    how it performs.  
2.User vs. System – defines who interacts with or enforces the requirement.


***A. Functional vs. Non-Functional Requirements***

| ID | Requirement Description | Type |
|----|--------------------------|------|
| R1 | Doctor can search for patient by National ID | Functional |
| R2 | Hospitals can upload medical reports | Functional |
| R3 | Patients can view their own medical records | Functional |
| R4 | All communication must be encrypted via HTTPS/TLS |Non-Functional |
| R5 | System must use Role-Based Access Control (RBAC) | Functional |
| R6 | Interface must support Arabic and English | Non-Functional |
| R7 | Database should allow real-time data retrieval | Non-Functional |
| R8 | Ministry can generate national health reports | Functional |
| R9 | System must log all data access and modification | Functional |
| R10 | System should maintain at least 99% uptime | Non-Functional |

***B. User vs. System Requirements***

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

3- Structured Specification (Mahmood Abdulasalam):

***Overview:***
This section specifies three critical functional requirements of the MedLink system, describing their purpose, inputs, outputs, and interactions with the system.

---

##### **Function: User Authentication and Access Control**  
**Related Requirements:** R5 (Role-Based Access Control), R4 (Data Encryption), R9 (Logging)  

**Description:**  
Authenticates users (doctors, administrators, and hospital staff) before granting access to the MedLink system. Ensures that only authorized personnel can view or modify patient data using secure, encrypted sessions.

**Inputs:**  
- **National ID** (verified unique identifier)  
- Password (strong, hashed in database)  
- Role type (doctor/admin)

**Source:**  
User login form on the MedLink web interface.

**Outputs:**  
- Authentication token (JWT)  
- Success or error message  
- Redirect to user dashboard

**Destination:**  
Backend authentication service (Ruby on Rails) and session controller.

**Action:**  
- Compares entered National ID and password with stored hashed values linked to that National ID in the database.  
- If credentials match and role permissions allow, generates a signed JWT token and establishes a session.  
- If credentials fail, returns an authentication error.  
- Logs the attempt in the audit system.

**Requires:**  
- Active database connection and existing user credentials linked to the National ID.  
- National ID must have been previously verified and associated with an active account.

**Precondition:**  
- User must be registered, National ID verified, and account active.

**Postcondition:**  
- Valid session token created for authenticated users.  
- Failed attempts are logged.

**Side Effects:**  
- Session timeout is triggered after 15 minutes of inactivity.  
- Multiple failed attempts may trigger account lockout or additional verification (as defined in security policy).

---

##### **Function: Patient Record Management**  
**Related Requirements:** R1 (Search Patient), R2 (Upload Reports), R3 (View Records), R9 (Logging)

**Description:**  
Allows authenticated doctors to create, read, and update patient medical records. Ensures data accuracy and integrity in the central PostgreSQL database.

**Inputs:**  
- Patient ID  
- Medical details (diagnosis, prescriptions, test results)  
- Doctor ID

**Source:**  
Doctor’s dashboard interface (React.js frontend).

**Outputs:**  
- Updated or retrieved patient record  
- Validation or error message

**Destination:**  
Central database and audit log system.

**Action:**  
- Verifies authorization and validates input data.  
- Performs the requested operation (insert, update, or retrieve).  
- Every update is timestamped and associated with the responsible doctor ID.  
- All actions are recorded for traceability.

**Requires:**  
Active database and proper access privileges.

**Precondition:**  
Doctor must be logged in and authorized.  
Patient record must exist or creation privileges must be granted.

**Postcondition:**  
Record successfully created, updated, or retrieved.  
Change is logged with timestamp and doctor ID.

**Side Effects:**  
Triggers data synchronization with backup server.

---

##### **Function: Inter-Hospital Data Sharing**  
**Related Requirements:** R6 (Multi-hospital integration), R4 (Encryption), R9 (Audit Logs)

**Description:**  
Enables hospitals connected to the MedLink network to securely share and retrieve patient medical records through encrypted APIs, ensuring continuity of care across different locations.

**Inputs:**  
- Hospital ID requesting data  
- Patient unique identifier (UUID)  
- Authorization token

**Source:**  
Authenticated API request from hospital system.

**Outputs:**  
- Encrypted patient record data  
- Error or denial message if unauthorized

**Destination:**  
Requesting hospital’s system and the MedLink audit log.

**Action:**  
- Validates the hospital’s identity and access permissions.  
- Encrypts and transmits requested data over HTTPS.  
- If permission or consent is missing, denies access and records the attempt.  
- Logs successful access events.

**Requires:**  
Both hospitals must be registered and have active network connection.

**Precondition:**  
Valid authentication token and patient consent for data sharing.

**Postcondition:**  
Requested data securely transmitted.  
Access event recorded in audit log.

**Side Effects:**  
Increases load on network bandwidth during high-traffic hours.

---

**Deliverable:**  
This document contains the structured specifications for three critical functional requirements of the MedLink project, fulfilling the responsibilities of the Structured Specification Developer role.


4.Requirement Prioritization
| Requirement ID | Description | Priority | Justification |
|----------------|--------------|-----------|----------------|
| R1 | Doctor can search for a patient by National ID | *M* | Core function for healthcare access |
| R2 | Hospitals can upload medical reports | *M* | Required for database updates |
| R3 | Patients can view their medical records | *M* | Improves transparency and patient engagement |
| R4 | All data encrypted via HTTPS/TLS | *M* | Critical for data protection and legal compliance |
| R5 | Role-based access control (RBAC) | *M* | Essential for user privacy and authorization |
| R6 | Multilingual interface (Arabic/English) | *N* | Improves accessibility for later versions |
| R7 | Real-time data retrieval | *N* | Boosts performance but not required initially |
| R8 | National health report generation | *N* | Important for government use, can come later |
| R9 | Audit logging of all access and changes | *M* | Required for compliance and traceability |
| R10 | 99% uptime reliability | *M* | Ensures hospital system availability |
| R11 | Doctor collaboration feature | *S (Superfluous)* | Useful but not necessary for first release |

*Legend:*  
- *M:* Mandatory (must be implemented in the first version)  
- *N:* Nice to Have (optional for later versions)  
- *S:* Superfluous (only if extra time/resources are available)


Conclusion 
The MedLink system establishes a unified, secure, and efficient medical database connecting hospitals, doctors, and patients nationwide. Through structured requirements engineering, the project ensures data integrity, privacy, and accessibility. Each functional element aligns with real-world healthcare needs, paving the way for safer and more connected medical services.
