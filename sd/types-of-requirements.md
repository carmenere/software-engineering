# Types of requirements
- **BR** (*Business Requirements*) - **Why** are we building this?
  - *Examples*:
    - Increase sales 20%.
- **FR** (*Functional Requirements*) - **What** must it do? They defines the behavior and business logic of the software.
  - *Examples*:
    - User can reset password.
- **NFR** (*Non-Functional Requirements*) - **How well** must it do it?
  - *Examples*:
    - All data at rest must be encrypted with AES-256.
    - Search results must return within 200ms for 95% of queries.
    - The system must be available 99.99% of the time.
    - A new user must complete checkout in under 3 minutes.
    - The system must support 1 million concurrent users.
- **RR** (*Reliability Requirements*) - **How well** it avoids/recover from failure? **One kind of NFR**.<br>
  - *Examples*:
    - 99.99999% uptime.
- **ASR** (*Architecture Significant Requirements*) - Any requirement (**FR** or **NFR**) that has a measurable impact on the architecture. **ASRs have long term consequences**.
  - *Examples*:
    - 1M concurrent users.
    - 99.99999% uptime.

<br>