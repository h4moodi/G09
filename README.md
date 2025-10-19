# G09
# MedLink - Iraq Unified Health Network

Authors: Mohammed Shazad  Zaid omer Mahmood abdulsalam Maad Kamal
Project Type: University Project  
Development Model: Incremental SDLC  
Backend: Ruby on Rails  
Frontend: React.js  
Database: PostgreSQL  

---

## About the Project

MedLink is a nationwide healthcare platform designed to connect all hospitals and clinics in Iraq through one unified digital system.  
It allows doctors and healthcare institutions to securely access patient medical records in real time from a central database.  

Currently, most hospitals in Iraq use paper records or isolated digital systems that do not communicate with each other.  
This makes it difficult to share important patient data between hospitals.  
MedLink solves this by providing a secure and centralized platform where all medical information can be stored, updated, and accessed when needed.

---

## Project Goal

The main goals of MedLink are to:
- Create a centralized system for sharing and storing medical records.  
- Help doctors make faster and more accurate decisions.  
- Improve cooperation between hospitals and healthcare professionals.  
- Build a secure and scalable system that can be expanded over time.  

---

## Why This Project

We chose this project because Iraq currently lacks a unified hospital database system.  
Creating one would improve healthcare efficiency, reduce duplicate tests, and make patient care faster and more accurate.  
It also helps me learn about real-world software design, database security, and system development.

---

## How It Works

1. Hospitals connect to the MedLink web platform.  
2. Doctors log in to access or update patient records.  
3. All data is stored securely in a PostgreSQL database.  
4. The Ruby on Rails backend handles requests, logic, and authentication.  
5. The React.js frontend provides a simple and clear dashboard for doctors and administrators.

---

## Technologies Used

| Component | Technology | Purpose |
|------------|-------------|----------|
| Backend | Ruby on Rails | Core logic, API, authentication |
| Database | PostgreSQL | Central data storage |
| Frontend | React.js | User interface |
| Authentication | Devise / JWT | Secure login system |
| SDLC Model | Incremental | Step-by-step development |

---

## Development Plan (Incremental SDLC)

The project will be built using the Incremental Software Development Life Cycle model.  
Each part of the system will be developed and tested before moving to the next stage.

| Stage | Focus | Expected Result |
|--------|--------|----------------|
| 1 | Core database and authentication system | Basic working backend |
| 2 | Patient record management | Doctors can view and update records |
| 3 | Hospital access and data sharing | Records accessible between hospitals |
| 4 | Reporting and analytics | Generate health insights and statistics |

---

## Security

Because MedLink handles medical data, security is a major focus.  
The system will:
- Use HTTPS/TLS for secure communication.  
- Encrypt sensitive data in the database.  
- Use role-based access (patients, doctors, admins).  
- Include audit logs to track who accesses patient data.  
- Be tested using simulated hospital data before deployment.  

---

## Risks

| Risk | Description | Solution |
|------|--------------|-----------|
| Data privacy | Medical data must remain confidential | Use encryption and strict access control |
| Scalability | The system may grow rapidly | Use modular and incremental design |
| Time limits | Large project scope | Focus on essential features first |

---

## Future Work

- Add integration with IoT health devices (for live readings).  
- Create a patient mobile app for easy access.  
- Add AI-based health analysis tools.  
- Include support for Arabic and Kurdish languages.  

---

## What We Will Learn

- How to build full-stack web applications using Ruby on Rails and React.js.  
- How to design and manage databases securely.  
- How to plan, test, and implement software using the Incremental SDLC model.  
- How to apply software engineering principles to solve real-world problems.  

---
