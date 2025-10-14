3.1 Architectural Design
 The architecture of ParhaiPartner follows a modular, multi-tiered (clientserver) design to en
sure scalability, maintainability, and clear separation of concerns. The system is decomposed
 into several interconnected modules that collaboratively achieve the desired functionality while
 maintaining flexibility for future extensions.
 3.1.1 Box and Line Diagram
 In the initial design stage, a simplified Box and Line diagram was created to visualize the major
 components of the system and the flow of data between them. The diagram represents users,
 frontend, backend, integrations, and database layers, showing how they interact to form the
 complete system.
 57
3. System Overview
 Figure 3.1: Box and Line Diagram for ParhaiPartner Architecture
 58
3.1 Architectural Design
 3.1.2 Detailed Architectural Design
 After finalizing the architecture, a more detailed representation was created to depict the mod
ular structure and flow between all system components. The architecture follows a multi-tiered
 clientserver approach, separating the system into four key subsystems: Users, Frontend, Back
end, and Database & Integrations.
 Figure 3.2: Detailed System Architecture
 3.1.2.1 Users Layer
 This layer represents the end-users of the system:
 • Student: Interacts with study plans, quizzes, payments, and university applications.
 • Teacher: Validates generated content and admission documents.
 • Counsellor: Manages student applications and document processing.
 59
3. System Overview
 3.1.2.2 Frontend Layer
 The frontend, built using React.js, provides a responsive interface for users and communicates
 with the backend via:
 • Axios API Calls: For fetching and updating data.
 • JWTAuthentication: Ensures secure user sessions.
 Componentssuch asReactHooksandmodularUIstates ensure smooth navigation and efficient
 data flow.
 3.1.2.3 Backend Layer
 Developed with the Django REST Framework, the backend manages business logic, data
 processing, and integration with external APIs. Major backend components include:
 • Authentication: Handles login, registration, and token management.
 • Analytics: Tracks user progress and performance.
 • Notes & Quiz Engines: Generate personalized notes and quizzes using AI.
 • Study Plan Engine: Builds and manages personalized learning plans.
 • Payment Manager: Processes financial transactions.
 • Email Notifier: Sends automated notifications and alerts.
 • Document Processor: Handles document uploads, formatting, and verification.
 • Application Manager: Manages and tracks university applications.
 3.1.2.4 Integration Layer
 This layer connects the backend to external intelligent and automation services:
 • Google Gemini (RAG): Supports AI-driven content generation.
 • Vector Database (FAISS/Pinecone): Enables contextual data retrieval for learning con
tent.
 • Payment API (Stripe/Paymob): Handles secure payment processing.
 • Google Drive API: Manages document storage and retrieval.
 • SMTP:Sends system-generated emails.
 60
3.2 Design Models
 3.1.2.5 Database Layer
 The PostgreSQL database stores all persistent data including user profiles, study plans, quiz
 results, and payment records. It ensures consistency and provides fast querying support for
 backend services.
 3.1.3 System Interaction Summary
 • The Frontend sends requests to the Backend via secure REST APIs.
 • The Backend processes business logic and interacts with the Database and Integra
tions.
 • Integrations (LLM, Payments, Google Drive, etc.) extend the system through AI au
tomation and external services.
 • All interactions are secured using JWT authentication and HTTPS.
 The modular design ensures scalability, maintainability, and the ability to independently en
hance components without affecting the entire system.
 3.2 Design Models
 Create design models as are applicable to your system. Provide detailed descriptions with each
 of the models that you add. Also ensure visibility of all diagrams.
 Design Models for Object Oriented Development Approach
 Theapplicable models for the project using object oriented development approach may include:
 Activity Diagram
 Class Diagram
 Class-level Sequence Diagram
 State Transition Diagram (for the projects which include event handling and backend processes)
 Design Models for Procedural Approach
 The applicable models for the project using procedural approach may include:
 Activity Diagram
 Data Flow Diagram (data flow diagram should be extended to 2-3 levels. It should clearly list
 all processes, their sources/sinks and data stores.)
 System-level Sequence Diagram
 61
3. System Overview
 State Transition Diagram (for the projects which include event handling and backend processes)
 62
3.2 Design Models
 3.2.1 Activity Diagrams
 3.2.1.1 Activity Diagram for Manage Profile
 Figure 3.3 illustrates the activity flow for the Manage Profile use case. The process begins
 when the actor (Student, Teacher, or Counsellor) logs into the ParhaiPartnerSystem and ac
cesses their profile. The actor can then view and edit relevant profile information, which varies
 by role type. The ParhaiPartnerSystem validates the submitted data and updates the stored
 information accordingly. Alternative paths are included for invalid input or duplicate email
 handling.
 Figure 3.3: Activity Diagram for Manage Profile Use Case
 63
3. System Overview
 3.2.1.2 Activity Diagram for Manage Payments
 Figure 3.4 illustrates the activity flow for the Manage Payments use case. This diagram cov
ers both the student and teacher/counsellor perspectives. Students view their connections and
 initiate payment for a specific month, while teachers and counsellors can access their payment
 history. The ParhaiPartner system processes transactions, updates records, and manages con
nection status based on successful or failed payments.
 Figure 3.4: Activity Diagram for Manage Payments Use Case
 64
3.2 Design Models
 3.2.1.3 Activity Diagram for Create Study Plans
 Figure 3.5 illustrates the activity flow for the Create Study Plans use case. The process be
gins when the student requests a new study plan, identifies the target exam, and specifies focus
 topics. Optionally, the student completes a diagnostic assessment to help the system generate
 a personalized plan. The LLM+RAG system retrieves syllabus data, analyzes the student pro
f
 ile, and produces a structured study plan. The student can review and adjust the plan before
 confirming. Alternative paths handle cases where the LLM service is unavailable, RAG data is
 missing, or the diagnostic assessment cannot be completed.
 Figure 3.5: Activity Diagram for Create Study Plans Use Case
 65
3. System Overview
 3.2.1.4 Activity Diagram for Generate Notes
 Figure 3.6 illustrates the activity flow for the Generate Notes use case. The process begins
 when the student requests notes for a particular topic and specifies content preferences such as
 detail level or length. The system retrieves relevant information from the RAG knowledge base
 and analyzes it. The LLM+RAG system then generates structured study notes with headings,
 key points, and examples. The student reviews and can request refinements before confirming
 the final notes. The ParhaiPartnerSystem saves the notes, forwards them for teacher validation,
 and ensures they are accessible for review, download, or export. Alternative paths are included
 for incomplete RAG data or temporary LLM service issues.
 Figure 3.6: Activity Diagram for Generate Notes Use Case
 66
3.2 Design Models
 3.2.1.5 Activity Diagram for Attempt Quizzes
 Figure 3.7 illustrates the activity flow for the Attempt Quizzes use case. The process begins
 when the student requests to take a quiz for a particular subject or topic. The ParhaiPartner
System verifies the assigned teacher and retrieves a validated quiz from the teachers question
 bank. The system then prepares and delivers the quiz to the student while tracking responses
 and timing. After submission, the ParhaiPartnerSystem calculates the score and compiles a per
formance report. The LLM+RAG System supports the process by generating AI-based expla
nations for incorrect answers, providing personalized feedback, and suggesting improvement
 strategies. The student can review detailed feedback, explore explanations, and ask follow
up questions through the integrated Doubt Solving feature. Finally, the ParhaiPartnerSystem
 updates the students progress metrics and shares summarized analytics with the teacher for re
view. Alternative flows manage scenarios such as quiz timeouts or temporary unavailability of
 the AI Doubt Solving feature.
 Figure 3.7: Activity Diagram for Attempt Quizzes Use Case
 67
3. System Overview
 3.2.1.6 Activity Diagram for Manage University Applications
 Figure 3.8 illustrates the activity flow for the Manage University Applications use case. The
 process begins when the student requests access to the application management feature. The
 ParhaiPartnerSystem checks whether a counsellor is assigned and enables collaborative re
view if applicable. The student initiates a new application, explores and compares universities,
 selects a preferred program, and submits preliminary information. The ParhaiPartnerSystem
 records the application and updates the status. If a counsellor is assigned, they review and pro
vide feedback, and the student updates the application accordingly. All revisions are logged,
 and the system maintains the application status. Alternative paths handle cases where counsel
lor involvement is conditional.
 Figure 3.8: Activity Diagram for Manage University Applications Use Case
 68
3.2 Design Models
 3.2.1.7 Activity Diagram for Build Admission Documents
 Figure 3.9 illustrates the activity flow for the Build Admission Documents use case. The
 process begins when the student requests to create a new admission document and selects the
 desired document type, such as a personal statement, essay, or recommendation letter request.
 The ParhaiPartnerSystem provides a suitable template and guiding questions to capture the stu
dents background, goals, and motivations. The LLM+RAG system uses this input to generate
 an initial draft, which the student reviews and refines as needed. If desired, the student may
 initiate a plagiarism check to ensure originality, and the system provides a similarity report with
 relevant highlights. Once finalized, the document is saved and uploaded to the students docu
ment repository. If a counsellor is assigned, the document is automatically shared for feedback
 and review. Alternative paths address issues such as file upload failures or unsupported file
 formats to ensure document integrity and completion.
 Figure 3.9: Activity Diagram for Build Admission Documents Use Case
 69
3. System Overview
 3.2.1.8 Activity Diagram for Manage Generated Learning Content
 Figure 3.10 illustrates the activity flow for the Manage Generated Learning Content use
 case. The process begins when the teacher requests access to pending learning materials. The
 ParhaiPartnerSystem displays two content categories: student-submitted notes and teacher
generated quiz questions. For student-submitted notes, the teacher selects a note, reviews it
 for accuracy, clarity, and relevance, provides feedback, and chooses to approve, reject, or re
quest revision. For teacher-generated quiz questions, the teacher specifies topic, difficulty, and
 quantity, after which the LLM+RAG system generates draft questions. The teacher reviews
 each question, approves, edits, or rejects them, and the approved questions are stored in the
 teachers question bank. All validation activities are logged and metrics are updated. Alter
native paths cover content retrieval failures, validation save errors, or question bank service
 unavailability.
 Figure 3.10: Activity Diagram for Manage Generated Learning Content Use Case
 70
3.2 Design Models
 3.2.1.9 Activity Diagram for Validate Admission Documents
 Figure 3.11 illustrates the activity flow for the Validate Admission Documents use case. The
 counsellor requests access to student-submitted documents pending validation. The ParhaiPart
nerSystem presents a list of documents organized by student and type. The counsellor selects
 a document, reviews its content, grammar, structure, formatting, and originality, and provides
 feedback and ratings. A validation decision is then made: approve, approve with suggestions,
 request revision, or reject. The system records the decision, notifies the student, and links
 approved documents to relevant applications. Alternative flows address document retrieval
 failures or student updates prior to review.
 Figure 3.11: Activity Diagram for Validate Admission Documents Use Case
 71
3. System Overview
 3.2.2 State Transition Diagrams
 3.2.2.1 State Transition Diagram for Manage Profile
 Figure 3.12 illustrates the state transitions for the Manage Profile use case. The process begins
 when the actor (Student, Teacher, or Counsellor) logs into the ParhaiPartnerSystem. Actors can
 access their profile, initiate edits, and submit changes. The system validates the input, handles
 invalid input or duplicate emails, updates profile data, and provides confirmation. The diagram
 includes all key components such as states, transitions, triggers, loops, and the final state.
 Figure 3.12: State Transition Diagram for Manage Profile Use Case
 72
3.2 Design Models
 3.2.2.2 State Transition Diagram for Manage Payments
 Figure 3.13 illustrates the state transitions for the Manage Payments use case. This diagram
 captures both student and teacher/counsellor perspectives. Students can view connections, au
thorize payments, and handle errors such as duplicate payments or payment system unavail
ability. Teachers and counsellors can review payment history and receipts. The system updates
 records, manages connection status, and ensures proper final states for all actors. The diagram
 emphasizes key components including states, transitions, triggers, loops, and final states.
 Figure 3.13: State Transition Diagram for Manage Payments Use Case
 73
3. System Overview
 3.2.2.3 State Transition Diagram for Create Study Plans
 Figure 3.14 illustrates the state transitions for the Create Study Plans use case. The student
 initiates a study plan request, optionally completes a diagnostic assessment, and the system
 retrieves syllabus data from RAG and generates a personalized plan. The student reviews and
 confirms the plan, which is then saved to the dashboard. Alternative flows handle missing RAG
 data, LLM service unavailability, or skipped diagnostic assessment.
 Figure 3.14: State Transition Diagram for Create Study Plans Use Case
 74
3.2 Design Models
 3.2.2.4 State Transition Diagram for Generate Notes
 Figure 3.15 illustrates the state transitions for the Generate Notes use case. The student re
quests notes, optionally specifies preferences, and the system retrieves data from RAG and
 generates structured notes. The student reviews, requests refinements if necessary, confirms
 the final notes, and the system forwards them for teacher validation. Alternative flows cover
 incomplete RAG data or LLM service unavailability.
 Figure 3.15: State Transition Diagram for Generate Notes Use Case
 75
3. System Overview
 3.2.2.5 State Diagram for Attempt Quizzes
 Figure 3.16 illustrates the state transitions for the Attempt Quizzes use case. The diagram
 begins with the student logging into the system. The student selects a quiz and reviews the
 overview before attempting it. Upon submission, the system evaluates performance, generates
 analytics, and provides AI-based doubt-solving support. Alternative flows handle quiz timeout,
 temporary unavailability of doubt solving, or deferred teacher review.
 Figure 3.16: State Diagram for Attempt Quizzes Use Case
 76
3.2 Design Models
 3.2.2.6 State Diagram for Manage University Applications
 Figure 3.17 illustrates the state transitions for the Manage University Applications use case.
 The process starts with the student logging in and accessing the university application module.
 The system verifies counsellor assignment, supports search and comparison of universities,
 and records application data. Counsellor feedback and student updates are incorporated before
 f
 inalizing the application. Alternative paths address missing university data and location service
 failures.
 Figure 3.17: State Diagram for Manage University Applications Use Case
 77
3. System Overview
 3.2.2.7 State Diagram for Build Admission Documents
 Figure 3.18 illustrates the state transitions for the Build Admission Documents use case. The
 process starts with the student logging in, selecting a document type, providing background
 information, and generating a draft using LLM+RAG. The student can revise the draft, option
ally run a plagiarism check, finalize, save, and upload the document. Alternative paths handle
 f
 ile upload failures or unsupported formats.
 Figure 3.18: State Diagram for Build Admission Documents Use Case
 78
3.2 Design Models
 3.2.2.8 State Diagram for Manage Generated Learning Content
 Figure 3.19 illustrates the state transitions for the Manage Generated Learning Content use
 case. The teacher logs in, selects pending content for validation, reviews student-submitted
 notes or teacher-generated quizzes, provides feedback, and the system records decisions. Al
ternative paths cover content load failures, validation save errors, and question bank service
 unavailability.
 Figure 3.19: State Diagram for Manage Generated Learning Content Use Case
 79
3. System Overview
 3.2.2.9 State Diagram for Validate Admission Documents
 Figure 3.20 illustrates the state transitions for the Validate Admission Documents use case.
 Thecounsellor logs in, selects a document to review, evaluates it, provides feedback, and selects
 a validation decision. The system records the decision and notifies the student. Alternative
 paths handle document retrieval failures and revisions made before review.
 Figure 3.20: State Diagram for Validate Admission Documents Use Case
 80
3.3 Data Design
 3.3 Data Design
 Explain how the information domain of your system is transformed into data structures. De
scribe how the major data or system entities are stored, processed, and organized.
 List any databases or data storage items.