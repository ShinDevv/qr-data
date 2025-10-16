
# MNHS Student Schedule Database

---


### 1. `students`
Stores student information.

| Column             | Type      | Description |
|--------------------|-----------|-------------|
| `student_id`       | INT (PK)  | Unique identifier (auto-increment). |
| `qr_data`          | VARCHAR   | QR code data for attendance. |
| `student_name`     | VARCHAR   | Full name of the student. |
| `grade_level`      | VARCHAR   | Grade level (e.g., "12"). |
| `section_id`       | INT (FK)  | Reference to `sections.section_id`. |
| `guardian_contact` | VARCHAR   | Guardian/parent phone number. |
| `lrn`              | VARCHAR   | Learner Reference Number (unique). |

---

### 2. `sections`
Represents class sections.

| Column         | Type      | Description |
|----------------|-----------|-------------|
| `section_id`   | INT (PK)  | Unique identifier (auto-increment). |
| `section_name` | VARCHAR   | Name of the section (e.g., "ICT-1"). |
| `grade_level`  | VARCHAR   | Grade level of the section. |

---

### 3. `subjects`
List of all subjects offered in the school.

| Column       | Type      | Description |
|--------------|-----------|-------------|
| `subject_id` | INT (PK)  | Unique identifier (auto-increment). |
| `subject_name` | VARCHAR | Subject name (e.g., "Java-Programming"). |

---

### 4. `section_subjects`
Mapping table to link sections with their specific subjects.

| Column          | Type      | Description |
|-----------------|-----------|-------------|
| `section_subject_id` | INT (PK) | Unique identifier (auto-increment). |
| `section_id`    | INT (FK)  | Reference to `sections.section_id`. |
| `subject_id`    | INT (FK)  | Reference to `subjects.subject_id`. |

---

### 5. `schedule`
Defines the class schedule for each section.

| Column       | Type      | Description |
|--------------|-----------|-------------|
| `schedule_id` | INT (PK) | Unique identifier (auto-increment). |
| `section_id` | INT (FK)  | Linked to `sections.section_id`. |
| `day`        | ENUM      | Day of the week (Mondayâ€“Saturday). |
| `period`     | INT       | Period number (1â€“8). |
| `time`       | VARCHAR   | Time range (e.g., "7:30 AM - 9:30 AM"). |
| `subject_id` | INT (FK)  | Linked to `subjects.subject_id`. |


