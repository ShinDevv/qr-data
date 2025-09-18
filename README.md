
# MNHS Student Schedule Database

---

## ðŸ“‚ Database Structure

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



## ðŸ—„ï¸ Sample Data

### Students
```sql
INSERT INTO students (student_id, qr_data, student_name, grade_level, section_id, guardian_contact, lrn) VALUES
(1, 'MNHS2025202600001', 'Jerence Charles Visperas', '12', 1, '+639318387130', '10181500000');

Sections

INSERT INTO sections (section_id, section_name, grade_level) VALUES
(1, 'ICT-1', '12'),
(2, 'STEM-1', '12');

Subjects

INSERT INTO subjects (subject_id, subject_name) VALUES
(1, 'Java-Programming'),
(2, 'Break-Time'),
(3, 'CPAR'),
(4, 'PR2'),
(5, 'Lunch-Break'),
(6, 'MIL'),
(7, 'PHILOSOPHY'),
(8, 'ELS'),
(9, 'Calculus'),
(10, 'Physics');

Section-Subjects

-- ICT-1 subjects
INSERT INTO section_subjects (section_subject_id, section_id, subject_id) VALUES
(1, 1, 1),
(2, 1, 2),
(3, 1, 3),
(4, 1, 4),
(5, 1, 5),
(6, 1, 6),
(7, 1, 7),
(8, 1, 8);

-- STEM-1 subjects
INSERT INTO section_subjects (section_subject_id, section_id, subject_id) VALUES
(9, 2, 2),
(10, 2, 5),
(11, 2, 9),
(12, 2, 10),
(13, 2, 7),
(14, 2, 6);

Schedule (Monday - ICT-1)

INSERT INTO schedule (schedule_id, section_id, day, period, time, subject_id) VALUES
(1, 1, 'Monday', 1, '7:30 AM - 9:30 AM', 1),
(2, 1, 'Monday', 2, '9:30 AM - 10:00 AM', 2),
(3, 1, 'Monday', 3, '10:00 AM - 11:00 AM', 3),
(4, 1, 'Monday', 4, '11:00 AM - 12:00 PM', 4),
(5, 1, 'Monday', 5, '12:00 PM - 1:00 PM', 5),
(6, 1, 'Monday', 6, '1:00 PM - 2:00 PM', 6),
(7, 1, 'Monday', 7, '2:00 PM - 3:00 PM', 7),
(8, 1, 'Monday', 8, '3:00 PM - 4:00 PM', 8);

```
---

ðŸ“Š Visualization

Example of Monday Schedule for ICT-1:

Period 1 â†’ 7:30 AM - 9:30 AM | Java-Programming  
Period 2 â†’ 9:30 AM - 10:00 AM | Break-Time  
Period 3 â†’ 10:00 AM - 11:00 AM | CPAR  
Period 4 â†’ 11:00 AM - 12:00 PM | PR2  
Period 5 â†’ 12:00 PM - 1:00 PM | Lunch-Break  
Period 6 â†’ 1:00 PM - 2:00 PM | MIL  
Period 7 â†’ 2:00 PM - 3:00 PM | PHILOSOPHY  
Period 8 â†’ 3:00 PM - 4:00 PM | ELS

---

