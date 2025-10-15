## Assumptions (UC-01 to UC-09)

### UC-01 Manage Profile
- Subjects: GET `subjects/`; teachers may POST `subjects/`.
- Update: PUT `/api/update-profile/` (partial), fields per `UserSerializer` + `subject_ids`.
- Email change via `/api/auth/change-email/` (not via profile PUT).

### UC-02 Manage Payments (Design)
- `Payment` model exists; linked to `Connection`.
- Endpoints: GET `/payments/overview`, POST `/payments/intent`, GET `/payments/history`.
- External gateway returns success/failure/duplicate.
- On success: mark connection active for month; send receipts.
- Overdue handling via scheduled backend job.

### UC-03 Create Study Plans (Implemented)
- Uses GET `/api/upcoming-tests/` then POST `/api/generate-study-plan/`.
- LLM returns valid grouped JSON; errors surfaced.
- Topics created with initial status; dates end before test.

### UC-04 Generate Notes (Implemented)
- Context uses nearest upcoming test type or GENERAL.
- Clean markdown via `clean_notes`; store as `Note`.
- Order: CustomNote → existing Note → LLM generate.

### UC-05 Attempt Quizzes (Design)
- `QuizAPI`: GET overview, POST submit responses.
- Source: teacher-validated question bank.
- Persist: `QuizResult`, `QuizAnswer`.
- LLM explanations for incorrect answers.

### UC-06 Manage Applications (Design)
- `ApplicationAPI`: GET `/applications`, GET `/universities?filters`, POST `/applications`, GET/PATCH `/applications/{id}`.
- Notify student on counsellor feedback.
- University data backed by repo dataset.

### UC-07 Build Documents (Design)
- `DocumentAPI`: templates + guiding questions.
- Draft via LLM; user reviews.
- Upload to Drive; save `drive_file_id` in `ApplicationDocument`.
- Link to `Application`.

### UC-08 Manage Learning Content (Design)
- `ContentAPI`: GET pending notes; POST decisions; POST generate questions.
- LLM drafts questions; teacher approves/edits/rejects.
- Store approved in question bank.

### UC-09 Validate Documents (Design)
- `ValidationAPI`: GET `/documents/pending`, GET `/documents/{id}`, POST decision.
- Link approved docs to `Application`; notify student.


