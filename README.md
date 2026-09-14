# Carieeer-System-Design
## 1. Project Overview

Career System is a platform that connects job seekers with
companies and job opportunities.

The system allows candidates to create profiles, manage their
information, search for jobs, and apply for suitable positions.

Companies can create company profiles, publish job opportunities,
and manage received applications.
## 2. System Goals

The main goals of the system are:

- Connect candidates with companies.
- Allow companies to publish job opportunities.
- Allow candidates to search and apply for jobs.
- Manage job applications and their statuses.
- Provide a structured and scalable system design.
  
## 3. Functional Requirements
The system provides the following main functionalities:

### Candidate

- Register and log in.
- Create and update candidate profile.
- Upload CV.
- Add LinkedIn profile.
- Search for available jobs.
- Apply for jobs.
- Track application status.

### Company

- Register and log in.
- Create and update company profile.
- Create job postings.
- Update and delete job postings.
- View received applications.
- Manage application status.

  ## 4. Non-Functional Requirements

The system should satisfy the following non-functional requirements:

- Security
- Scalability
- Performance
- Availability
- Maintainability
- Reliability
  
  Detailed functional and non-functional requirements are documented in:
  <img width="945" height="989" alt="requirements" src="https://github.com/user-attachments/assets/61b1d153-c5df-4806-8060-b8ca5b5fc60b" />

  ## 5. Data Model

The main entities in the system include:
Data model:
1- user(id-email-password-role-cteated at - updated at- status-last login)
2-cndidate profile(candidate id- user id-headline-bio-phone-location-
birth date- experience years- CV URL- LinkedIn URL- created at- updated at)
3- company(id-name-descreption-industry-location-website URL-status-created at -upadted at)
4-job(job id-company id-title-description-location-min salary-max salary-
        expereience level-status-employment type-work mode)
5-skills(id-name-category-description)
6-job skills(job id-skill id -required-proficiency)
7-application(id-candidate id-job id-status-letter-cv URL-applied at)
8-candidate skills(candidate id-skill id-proficiency level-expereience years)
9-candidate goal(candidate id-goal id-title - descreotion-target date) 
10-expereience(expereince id-candidate id- company name-job title- description-start date-end date)





