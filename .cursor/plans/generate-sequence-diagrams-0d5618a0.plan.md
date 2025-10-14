<!-- 0d5618a0-edac-4be0-b2c1-d7b1584547bc 44a01d45-869d-496c-9d8c-a7c4ca5c04f3 -->
# Generate Sequence Diagrams for ParhaiPartner Use Cases

## Approach

- Create sequence diagrams one by one for each use case
- Ask clarifying questions before generating each SD
- Get user confirmation after each SD before proceeding
- Follow specifications:
- **1c**: Show specific view classes/functions as separate participants
- **2b**: Simplified external actors (LLM, Payment System, Google Drive)
- **3b**: Database operations implicit within backend
- **4b**: Simplified REST API calls without endpoint details
- **5a**: Design-level SDs based on use case specifications
- read all the relevant files before writing the code for a use case.

## Use Cases to Cover

1. **UC-01**: Manage Profile (Student, Teacher, Counsellor)
2. **UC-02**: Manage Payments
3. **UC-03**: Create Study Plans
4. **UC-04**: Generate Notes
5. **UC-05**: Attempt Quizzes
6. **UC-06**: Manage University Applications
7. **UC-07**: Build Admission Documents
8. **UC-08**: Manage Generated Learning Content
9. **UC-09**: Validate Admission Documents

## Process for Each Use Case

1. Analyze use case specification and implementation
2. Ask clarifying questions if needed
3. Create Mermaid sequence diagram
4. Present to user for confirmation
5. Move to next use case after approval

## Key Participants to Use

- **Actor**: Student/Teacher/Counsellor (role-based)
- **Frontend**: React components
- **Backend Views**: Specific view classes/functions (e.g., `UpdateProfileView`, `RegisterView`)
- **External Systems**: `LLM System`, `Payment System`, `Google Drive API`
- **Serializers**: Django serializers where relevant
- **Models**: Django models for data validation

## Diagram Structure

- Start with actor initiating action
- Show REST API calls (simplified)
- Show view processing and validation
- Show external system interactions (simplified)
- Include alternative flows for errors
- End with response back to actor

### To-dos

- [ ] Create SD for UC-01: Manage Profile (all actors)
- [ ] Create SD for UC-02: Manage Payments
- [ ] Create SD for UC-03: Create Study Plans
- [ ] Create SD for UC-04: Generate Notes
- [ ] Create SD for UC-05: Attempt Quizzes
- [ ] Create SD for UC-06: Manage University Applications
- [ ] Create SD for UC-07: Build Admission Documents
- [ ] Create SD for UC-08: Manage Generated Learning Content
- [ ] Create SD for UC-09: Validate Admission Documents