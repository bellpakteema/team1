
erDiagram
    STUDENT {
        int student_id PK
        string student_name
        string student_email
        string student_class
        string student_phone
    }

    TEACHER {
        int teacher_id PK
        string teacher_name
        string teacher_email
        string department
    }

    COMPETITION {
        int competition_id PK
        string competition_name
        string competition_detail
        date start_date
        date end_date
        string location
        string status
    }

    CATEGORY {
        int category_id PK
        string category_name
        string category_detail
    }

    ENTRY {
        int entry_id PK
        int competition_id FK
        int category_id FK
        int teacher_id FK
        string entry_name
        date register_date
        string entry_status
    }

    ENTRY_MEMBER {
        int entry_member_id PK
        int entry_id FK
        int student_id FK
        string member_role
    }

    WORK {
        int work_id PK
        int student_id FK
        string work_name
        string work_detail
        string work_type
        string work_url
        date created_date
    }

    JUDGE {
        int judge_id PK
        string judge_name
        string judge_expertise
        string judge_email
    }

    JUDGING {
        int judging_id PK
        int entry_id FK
        int judge_id FK
        float score
        string comment
        date judging_date
    }

    AWARD {
        int award_id PK
        int entry_id FK
        string award_name
        string award_detail
        date award_date
    }

    COMPETITION ||--o{ ENTRY : has
    CATEGORY ||--o{ ENTRY : classifies
    TEACHER ||--o{ ENTRY : advises
    ENTRY ||--|{ ENTRY_MEMBER : contains
    STUDENT ||--o{ ENTRY_MEMBER : participates
    STUDENT ||--o{ WORK : creates
    ENTRY ||--o{ JUDGING : receives
    JUDGE ||--o{ JUDGING : evaluates
    ENTRY ||--o| AWARD : receives
