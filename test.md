```mermaid
erDiagram
direction LR
    SUBJECT {
        string subject_id
        string subject_name
    }
    CHAPTER {
        string chapter_id
        string chapter_name
        string subject_id
    }
    QUESTION {
        string question_id
        string question_content
        string option_a
        string option_b
        string option_c
        string option_d
        string chapter_id
    }
    EXAM {
        string exam_id
        date exam_date
        string subject_id
    }
    EXAM_QUESTION {
        string exam_id
        string question_id
    }
    STUDENT {
        string student_id
        string student_name
        string student_address
        string class_id
    }
    CLASS {
        string class_id
        string class_name
    }
    CLASS_SUBJECT {
        string class_id
        string subject_id
    }
    STUDENT_ANSWER {
        string student_id
        string exam_id
        string question_id
        string answer_choice
    }
    SUBJECT ||--o{ CHAPTER : includes
    CHAPTER ||--o{ QUESTION : contains
    SUBJECT ||--o{ EXAM : has
    EXAM ||--o{ EXAM_QUESTION : includes
    EXAM_QUESTION }o--|| QUESTION : contains
    CLASS ||--o{ STUDENT : has
    CLASS ||--o{ CLASS_SUBJECT : studies
    CLASS_SUBJECT }o--|| SUBJECT : includes
    STUDENT ||--o{ STUDENT_ANSWER : submits
    EXAM ||--o{ STUDENT_ANSWER : contains
    STUDENT_ANSWER }o--|| QUESTION : answers
