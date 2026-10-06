# Система реєстрації студентів та навчального процесу

## Опис проєкту:

- Система реєстрації студентів та навчального процесу створена для організації процесу реєстрації студентів на курси, автоматизації обліку студентів, їхньої успішності, викладачів, груп, спеціальностей та дисциплін.
- Система повинна зберігати інформацію про структуру навчального закладу, студентів та викладачів; встановлювати зв'зяки між ними; реєструвати студентів на навчальні курси; зберігати результати їхнього навчання.

## Бізнес-логіка:

- Факультет може мати декілька кафедр та спеціальностей, проте кожна кафедра та спеціальність закріплена за одним факультетом.
- На кожній спеціальності може навчатися декілька навчальних груп.
- Студент належить тільки до однієї групи.
- Викладач належить тільки до однієї кафедри.
- Кожен курс закріплений за однією кафедрою.
- Студент може бути зареєстрований на декілька курсів.
- Студент не може бути зареєстрований на певний курс більш ніж один раз.
- Оцінка за курс має бути від 0 до 100 балів.

## ERd:

```mermaid
erDiagram
    FACULTY {
        number faculty_id PK
        string faculty_name
        string short_name
        number building_number
        string phone
        string email UK
        string dean_name
    }

    DEPARTMENT {
        number department_id PK
        string department_name
        string short_name
        number room_number
        string phone
        string email UK
        string head_name
        number faculty_id FK
    }

    SPECIALTY {
        number specialty_id PK
        string specialty_name
        string specialty_code UK
        string education_level
        string study_form
        number study_duration
        number faculty_id FK
    }

    GROUP {
        number group_id PK
        string group_name
        number admission_year
        number course_year
        string study_form
        string curator_name
        number specialty_id FK
    }

    STUDENT {
        number student_id PK
        string full_name
        date birth_date
        string gender
        string email UK
        string phone
        string address
        date admission_date
        string study_status
        number group_id FK
    }

    TEACHER {
        number teacher_id PK
        string full_name
        string email UK
        string phone
        string academic_title
        string academic_degree
        string position
        number work_experience
        number department_id FK
    }

    COURSE {
        number course_id PK
        string course_name
        string course_code UK
        number ects_credits
        number hours
        string assessment_type
        number semester
        string description
        number department_id FK
    }

    ENROLLMENT {
        number enrollment_id PK
        number student_id FK "UNIQUE(student_id, course_id)"
        number course_id FK "UNIQUE(student_id, course_id)"
        number teacher_id FK
        date enrollment_date
        number grade "CHECK 0..100"
        string status
        string comment
    }

    FACULTY ||--o{ DEPARTMENT : "містить (1:N)"
    FACULTY ||--o{ SPECIALTY : "містить (1:N)"
    SPECIALTY ||--o{ GROUP : "містить (1:N)"
    GROUP ||--o{ STUDENT : "містить (1:N)"
    DEPARTMENT ||--o{ TEACHER : "містить (1:N)"
    DEPARTMENT ||--o{ COURSE : "містить (1:N)"
    STUDENT ||--o{ ENROLLMENT : "має (1:N)"
    COURSE ||--o{ ENROLLMENT : "містить (1:N)"
    TEACHER ||--o{ ENROLLMENT : "відповідає (1:N)"

<!-- PR review branch -->