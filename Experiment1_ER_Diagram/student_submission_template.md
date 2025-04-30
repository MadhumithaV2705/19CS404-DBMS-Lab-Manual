## ER DIAGRAM SUBMISSION 
## NAME - Madhumitha V
## REGISTER NUMBER - 212223060145

## SCENARIO CHOSEN:
Hospital ER Diagram

## ER DIAGRAM:
![WhatsApp Image 2025-03-06 at 16 59 45_fea08594](https://github.com/user-attachments/assets/2af6ff0b-07af-45e2-a8dd-4d098165f658)

## ENTITIES AND ATTRIBUTES:
~~~
Patient - Patient_ID (PK), Name, Gender, Date of Birth (DoB), Address, Phone No., Email, Insurance

Doctor - ID (PK), Name, Specialization, Phone No., Email, Work Schedule

Appointment - Appointment_ID (PK), Date, Time

Medical Records - ID (PK), Diagnosis

Billing - Billing_ID (PK), Patient_ID (FK), Amount, Billing Date, Payment Status

Department - Dept_ID (PK), Dept_Name, Dept_Head, Room No.
~~~
## RELATIONSHIPS AND CONSTRAINS:

## Book (Patient → Appointment)
Cardinality: Many-to-Many
Participation: Total (Every appointment must involve at least one patient)

## Assign (Appointment → Doctor)
Cardinality: Many-to-One
Participation: Total (Each appointment must be assigned to a doctor)

## Associate (Patient → Medical Records)
Cardinality: One-to-Many
Participation: Partial (A patient may or may not have medical records)

## Maintain (Doctor → Medical Records)
Cardinality: One-to-Many
Participation: Partial (Doctors maintain multiple records)

## Receive (Patient → Billing)
Cardinality: One-to-Many
Participation: Partial (Patients may have multiple billing records)

## Specialization (Doctor → Department)
Cardinality: Many-to-One
Participation: Partial (Doctor specializes in a department)

## EXTENSION (Prerequisite / Billing):

- **Billing Modeling Approach**:
  - The **Billing** entity is connected to the **Patient** entity via a **"Receive"** relationship.
  - This relationship represents that **billing entries are generated** for each patient **based on services received**.

- **Billing Entity Attributes**:
  - **Billing_ID** – Unique identifier for each billing entry.
  - **Amount** – The monetary value associated with the services rendered.
  - **Billing Date** – The date when the billing entry was generated.
  - **Payment Status** – Indicates whether the bill has been paid, is pending, or overdue.

- **Entity Relationship Note**:
  - **Billing** tracks financial transactions **independently**.
  - Each billing entry is **linked to the Patient** via the **Patient_ID** foreign key.

## DESIGN CHOICES:

- **Core Entities**:
  - **Patient**, **Doctor**, and **Appointment** are foundational entities in any healthcare system and were thus naturally included.

- **Medical Records**:
  - Managed as a **separate entity** for flexibility.
  - Enables support for **multiple diagnoses** per patient and doctor.

- **Billing**:
  - Kept **separate from medical services** to maintain clear and organized **financial records**.
  - Ensures **independence between healthcare services** and financial operations.

- **Departments**:
  - Created for **Doctors** to reflect the **organizational hierarchy** and **specializations** within the healthcare facility.

- **Many-to-Many Relationships**:
  - Relationships like **Book (Patients ↔ Appointments)** and **Assign (Doctors ↔ Appointments)** are managed through **associative entities** (e.g., **Appointment**).
  - This simplifies **complex scheduling** and relationship management.

## RESULT:
Thus, the ER diagram for the hospital management system was successfully designed, and the entities, relationships, and constraints were clearly represented.
