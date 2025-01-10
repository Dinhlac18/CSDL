flowchart LR
    SUBJECT -->|includes| CHAPTER
    CHAPTER -->|contains| QUESTION
    SUBJECT -->|has| EXAM
    EXAM -->|includes| EXAM_QUESTION
    EXAM_QUESTION -->|contains| QUESTION
    CLASS -->|has| STUDENT
    CLASS -->|studies| CLASS_SUBJECT
    CLASS_SUBJECT -->|includes| SUBJECT
    STUDENT -->|submits| STUDENT_ANSWER
    EXAM -->|contains| STUDENT_ANSWER
    STUDENT_ANSWER -->|answers| QUESTION
    
    subgraph SUBJECT ["SUBJECT"]
        direction TB
        subject_id --> subject_name
    end
    
    subgraph CHAPTER ["CHAPTER"]
        direction TB
        chapter_id --> chapter_name --> subject_id
    end

    subgraph QUESTION ["QUESTION"]
        direction TB
        question_id --> question_content
        question_content --> option_a --> option_b --> option_c --> option_d --> chapter_id
    end

    subgraph EXAM ["EXAM"]
        direction TB
        exam_id --> exam_date --> subject_id
    end

    subgraph EXAM_QUESTION ["EXAM_QUESTION"]
        direction TB
        exam_id --> question_id
    end

    subgraph STUDENT ["STUDENT"]
        direction TB
        student_id --> student_name --> student_address --> class_id
    end

    subgraph CLASS ["CLASS"]
        direction TB
        class_id --> class_name
    end

    subgraph CLASS_SUBJECT ["CLASS_SUBJECT"]
        direction TB
        class_id --> subject_id
    end

    subgraph STUDENT_ANSWER ["STUDENT_ANSWER"]
        direction TB
        student_id --> exam_id --> question_id --> answer_choice
    end


