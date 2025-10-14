 UseCase Diagram and Extended Use Cases
 ParhaiPartner serves four primary actors: Students, Teachers, Counsellors, and System

  The ParhaiPartner system involves four main actors Students, Teachers, Counsellors, and
 external systems such as the Payment System and LLM + RAG System. Each actor interacts
 with the system to perform specific tasks that contribute to the overall learning and application
 management process. The following describes each actors interaction with the system and their
 corresponding use cases.
 2.1.1.1 Student
 Students are the primary users of the ParhaiPartner platform. They interact with multiple mod
ules to manage their academic and admission-related activities. Their major use cases include:
 • Manage Profile: Students can update their personal details, academic information, and
 preferences.
 • ManagePayments: Studentscanhandlefee-relatedtransactions andsubscriptions through
 the integrated Payment System.
 • Create Study Plans: They can design personalized study schedules to track progress
 and meet learning goals.
 • Generate Notes: Students can automatically generate topic-specific study notes with the
 help of the integrated LLM + RAG system.
 • AttemptQuizzes: Theycantest their understanding by attempting AI-generated quizzes
 linked to their study plans.
 • Manage University Applications: Students can prepare and monitor their university
 admission applications.
 • Build Admission Documents: They can create essential documents such as Statements
 of Purpose, recommendation letters, and resumes.
 2.1.1.2 Teacher
 Teachers play a supporting and evaluative role within the system. Their interactions mainly
 focus on content validation and student evaluation:
 • Manage Generated Learning Content: Teachers review and manage AI-generated
 content such as notes and quizzes to ensure academic quality.
 10
2.1 Use Case Diagram and Extended Use Cases
 • Validate Admission Documents: They verify and provide feedback on student admis
sion documents to maintain accuracy and credibility.
 • Generate Notes and Attempt Quizzes: Teachers may also test system-generated con
tent and quizzes to validate their educational value.
 2.1.1.3 Counsellor
 Counsellors are responsible for assisting students with the admission process and ensuring the
 authenticity of academic records. Their key use cases include:
 • ManageUniversity Applications: Counsellors help students shortlist and track suitable
 universities.
 • Build Admission Documents: They assist in constructing strong and persuasive admis
sion documents.
 • Validate Admission Documents: Counsellors review and approve final documents be
fore submission to universities.
 2.1.1.4 Payment System (External Actor)
 The Payment System handles all financial transactions within the ParhaiPartner platform. It is
 integrated to support:
 • Manage Payments: Secure processing of student payments, subscription fees, and re
lated financial activities.
 2.1.1.5 LLM + RAGSystem(External Actor)
 The Large Language Model (LLM) and Retrieval-Augmented Generation (RAG) System
 is an intelligent backend component used to support AI-driven academic tools:
 • Generate Notes: It produces personalized study notes based on course content and top
ics.
 • Attempt Quizzes: It creates dynamic quizzes for practice and self-assessment.
 • ManageGeneratedLearningContent: It assists in generating and refining educational
 materials.
 11
2. Project Requirements
 2.1.1.6 Summary
 The ParhaiPartner use case diagram demonstrates a comprehensive system where students
 are at the center, supported by teachers and counsellors, while AI and payment systems act as
 powerful enablers. Each interaction contributes to an efficient, automated, and student-centric
 learning and admission management environment



 Use Case 1: Manage Profile
 Use Case ID
 UC-01
 Use Case Name
 Manage Profile
 Scope
 ParhaiPartner
 Actor(s)
 Student (primary), Teacher (primary), Counsellor (primary)
 Description
 Actor creates, views, updates, and manages their personal or pro
fessional profile including background information, preferences,
 qualifications, and account settings. Content varies based on actor
 type.
 Preconditions
 • Actor has registered an account
 • Actor has completed account verification (email)
 Postconditions
 • Profile information is updated and stored in the system
 • For Teacher: subject expertise reflected in content assign
ment
 • Dashboard reflects updated profile information
 12
2.1 Use Case Diagram and Extended Use Cases
 Main Success Sce
nario (Basic Flow)
 1. The actor accesses the system using valid credentials
 2. Actor requests access to their profile information
 3. The system provides the actors current profile information
 4. The actor initiates the profile editing process
 5. The actor updates personal details such as name, email, and
 phone number
 6. Student-specific:
 • Updates educational background (institution, grade
 level, subjects)
 • Adds or updates profile picture (optional)
 Teacher-specific:
 • Updates professional details (qualifications, experi
ence)
 • Defines subjects and areas of expertise
 Counsellor-specific:
 • Definesspecialization areas (eg. career counseling, ad
missions)
 • Sets consultation rates (if applicable)
 7. The actor confirms and submits the changes
 8. The system validates the entered information
 9. The system updates the stored profile data accordingly
 10. The system acknowledges the successful update with a con
f
 irmation message
 13
2. Project Requirements
 Alternative Flows
 • A1: Invalid Input– At Step 5, if any required information is invalid or
 missing, the system identifies the issues and requests
 correction.
 • A2: Duplicate Email– At Step 5, if the updated email already exists for an
other account, the system informs the actor and re
quests an alternate email.
 Table 2.1: Use Case 1: Manage Profile (All Actors)
 14
2.1UseCaseDiagramandExtendedUseCases
 2.2.1.2 UseCase2:ManagePayments
 UseCaseID UC-02
 UseCaseName ManagePayments
 Scope ParhaiPartner
 Actor(s) Student(primary),Teacher(primary),Counsellor(primary),Pay
mentSystem(secondary)
 Description Managesmonthlypaymentsbetweenstudentsandassignedteach
ersor counsellors. Studentspaymonthlywages inadvance to
 maintain their active connectionwith a teacher or counsellor.
 Teachersandcounsellorscanviewtheirpaymenthistory,while
 thesystemmonitorspaymentstatusandconnectionvalidity. Ifa
 studentfailstopaybeforetheduedate, thesystemautomatically
 suspendsorterminatestheconnection.
 Preconditions
 •Actorisloggedintothesystem
 •Connection between student and teacher/counsellor has
 beenestablishedwithanagreedmonthlyrate
 • Paymentgateway/systemisfunctional
 • Paymentmethodisregisteredandvalid
 Postconditions
 • Paymenttransactionissuccessfullyprocessedandrecorded
 •Activeconnectionbetweenstudentandteacher/counselloris
 confirmedorrenewedforthepaidperiod
 • Ifpaymentfailsorisnotmadebytheduedate, theconnec
tionissuspendedorterminated
 •Receipts are generated and emailed toboth student and
 teacher/counsellor
 15
2.ProjectRequirements
 Main Success Sce
nario(BasicFlow) 1. StudentFlow:
 (a) Thestudentrequestsaccesstotheirpaymentinforma
tion.
 (b) Thesystemprovidesasummaryofallactiveandpend
ingteacherorcounsellorconnectionswith:
 •Connectiondetails(Name,Subject,Duration)
 •Monthlyrateandduedate
 • Paymentstatus(Paid/Unpaid/Overdue)
 (c) Thestudent identifies theconnectionforwhichpay
mentistobemade.
 (d) TheSystemprovidesapaymentsummarycontaining:
 •Connectionduration(1month)
 • Totalamountdue
 • Paymentmethod
 •Duedate
 (e) Thestudentauthorizesthepaymenttransaction.
 (f) Thesystemsubmitsthepaymentrequest totheexter
nalpaymentserviceforprocessing.
 (g) The payment service validates the transaction and
 communicatestheresulttothesystem.
 (h) Systemupdates:
 • Paymentrecord
 •ConnectionstatustoActiveforthepaidmonth
 (i) Thesystemissuesdigital receiptsandsends themto
 thestudentandtheassociatedteacherorcounsellor.
 16
2.1UseCaseDiagramandExtendedUseCases
 2. Teacher/CounsellorFlow:
 (a) Theteacherorcounsellorrequestsaccesstotheirpay
mentrecords.
 (b) Thesystemprovides thepayment historyassociated
 withallconnectedstudents.
 (c) Teacher/Counsellor reviews transaction details, in
cluding:
 • Studentname
 •Monthandamountpaid
 • Paymentdate
 •Connectionstatus(Active/Inactive)
 (d) Theteacherorcounsellormayrequestcopiesofdigital
 receiptsforrecordkeepingorreference..
 3. Systemmaintainsandsynchronizespaymentandconnection
 recordsacrossalllinkedaccounts.
 AlternativeFlows
 •A1:PaymentSystemUnavailable–AtStep7, if thepayment systemisunavailable, the
 systeminformsthestudentaboutincompletepayment
 processing.
 •A2:DuplicatePaymentAttempt–AtStep6, ifaduplicatepayment isdetectedfor the
 samebillingcycle, thesystempreventsdoublecharg
ingandalertsthestudent.
 •A3:UnpaidorOverdueStatus–Ifpayment isnotcompletedbytheduedate, thesys
temautomaticallysuspendsor terminates therelated
 connectionandnotifiesbothparties.
 Table2.2: UseCase2: ManagePayments (MonthlyAd
vanceModel)
 17
2.ProjectRequirements
 2.2.2 Student-SpecificUseCases
 2.2.2.1 UseCase3:CreateStudyPlans
 UseCaseID UC-03
 UseCaseName CreateStudyPlans
 Scope ParhaiPartner
 Actor(s) Student(primary),LLM+RAGSystem(secondary)
 Description Student requestsapersonalizedstudyplanbasedontargetexam,
 timeline,andcurrentknowledgelevel.ThesystemutilizesaLarge
 LanguageModel (LLM)withRetrieval-AugmentedGeneration
 (RAG)toproduceasyllabus-alignedandadaptivestudyplan.
 Preconditions
 • Studentisloggedintothesystem
 • Studenthascompletededucationalbackgroundprofile
 • Targetexaminformationisavailableinthesystem
 •RAGknowledgebasecontainsrelevantsyllabusdata
 • StudenthasaddedthetargettestinUpcomingTestssection
 Postconditions
 • Studyplanisgeneratedandsavedtostudent’sdashboard
 •Calendarisupdatedwithstudymilestones
 •Notificationsarescheduledforupcomingtopics
 • Progresstrackingisinitialized
 18
2.1UseCaseDiagramandExtendedUseCases
 Main Success Sce
nario(BasicFlow) 1. Thestudentrequeststocreateanewstudyplan.
 2. Thestudentidentifiesthetargetexam(e.g.,MDCAT,ECAT,
 NTS,SAT).
 3. Studentspecifiestopicstofocuson.
 4. Thestudentmayoptionallycompleteadiagnosticassess
menttogaugecurrentknowledgelevel.
 5. Thesystemretrievesrelevant syllabusandtopicdatafrom
 theRAGknowledgebase.
 6. Thesystemanalyzes thestudentsprofile,preferences, and
 diagnosticresults.
 7. Thesystemgeneratesastructuredstudyplanwithtopics,
 subtopics,andsuggestedtimelines.
 8. Thesystemprovides thegeneratedplantothestudent for
 review.
 9. Thestudentreviewsandrefinestheplanbyadjustingprior
itiesorstudyintensity.
 10. Thestudentconfirmsthefinalizedplan.
 11. Thesystemrecordstheplanandupdatesthestudentscalen
dar
 19
2. Project Requirements
 Alternative Flows
 • A1: LLMService Unavailable– At Step 7, if the LLM service fails or times out, the
 system notifies the student and allows retry once the
 service is restored.
 • A2: Missing RAG Data– At Step 5, if no syllabus information is retrieved, the
 system generates a default plan template using stan
dard subject data from the LLM.
 • A3: Diagnostic Assessment Unavailable– At Step 4, if the diagnostic quiz cannot be generated
 or accessed, the plan is produced based solely on the
 students existing profile data.
 Table 2.3: Use Case 3: Create Study Plans
 20
2.1UseCaseDiagramandExtendedUseCases
 2.2.2.2 UseCase4:GenerateNotes
 UseCaseID UC-04
 UseCaseName GenerateNotes
 Scope ParhaiPartner
 Actor(s) Student(primary),LLM+RAGSystem(secondary)
 Description StudentrequestsAI-generatedstudynotesforspecifictopics.The
 systemusesLLMwithRAGtocreatecomprehensive, structured
 notesthatalignwithcurriculumrequirements.
 Preconditions
 • Thestudentisauthenticatedwithinthesystem
 • Theselectedsubjectortopicexistsinthesystemdatabase
 • TheRAGknowledgebasecontains sufficient educational
 materialrelatedtothetopic.
 Postconditions
 • Thegeneratednotesarestoredinthestudentspersonal li
brary
 •Notesaremarkedforteachervalidation
 • Thestudent canimmediatelyaccess, review, ordownload
 thegeneratednotes
 •Notesremainavailableforexportorfurtherediting
 21
2.ProjectRequirements
 Main Success Sce
nario(BasicFlow) 1. Thestudentrequeststogeneratestudynotesforaparticular
 topic.
 2. Thestudentspecifiesanycontentpreferences,suchasdetail
 levelornotelength.
 3. Thesystemretrievesrelevant informationandsourcemate
rialfromtheRAGknowledgebase.
 4. Thesystemanalyzestheretrieveddataandgeneratesstruc
turededucationalnotes.
 5. Thesystemorganizesthecontentwithlogicalheadings,key
 points,andillustrativeexamples.
 6. Thesystemprovidesthegeneratednotestothestudent for
 review.
 7. Thestudent reviews thegeneratednotesandmayrequest
 refinementorregenerationifdesired.
 8. Thestudentconfirmsandsaves thefinalizednotes totheir
 personallibrary.
 9. Thesystemforwardsthenotesforteachervalidation.
 AlternativeFlows
 •A1:LLMServiceUnavailable–AtStep4,iftheLLMgenerationservicefailsortimes
 out,thesystemnotifiesthestudentaboutthesituation.
 •A2:IncompleteRAGData–AtStep3, if theRAGretrieval returns limitedorno
 results,thesystemgeneratesasimplifiedoutlineusing
 LLMonlyandinformsthestudentthatadditionaldata
 isbeingsourcedatthesystem’send.
 Table2.4:UseCase4:GenerateNotes
 22
2.1UseCaseDiagramandExtendedUseCases
 2.2.2.3 UseCase5:AttemptQuizzes(withPerformanceAnalyticsandDoubtSolving)
 UseCaseID UC-05
 UseCaseName AttemptQuizzes
 Scope ParhaiPartner
 Actor(s) Student(primary),Teacher(secondary),LLM+RAGSystem(sup
porting)
 Description This use case enables a student to attempt quizzes for self
assessment on selected subjects or topics. The system re
trievesvalidatedquizzesfromtheteachersquestionbank,andthe
 LLM+RAGsystemmayadaptquestions, generatehints, orpro
videAI-basedexplanations. Uponcompletion, thesystempro
videsdetailedperformanceanalyticsandactivates theAIDoubt
 Solvingfeatureforpost-quizlearning.
 Preconditions
 • Thestudentisauthenticatedwithinthesystem.
 • Theteacherhascreatedandvalidatedaquizfortheselected
 subjectortopic.
 • TheLLM+RAGmoduleisavailableforadaptiveanalytics
 anddoubtsolving.
 Postconditions
 • Thecompletedquizattemptisrecordedinthesystem.
 • Thestudentsperformanceanalyticsandpersonalizedfeed
backaregenerated.
 • The teacher receivesanoverviewof student performance
 metrics.
 • Student progressdataand improvement recommendations
 areupdatedonthedashboard.
 23
2.ProjectRequirements
 Main Success Sce
nario(BasicFlow) 1. Thestudentrequeststotakeaquizforaselectedsubjector
 topic.
 2. Thesystemverifiesconnectionwiththerelevantteacher.
 3. Thesystemretrieves thevalidatedquiz fromthe teachers
 questionbank.
 4. Thestudent reviews thequizoverviewandbegins theat
tempt.
 5. Thesystempresentsthequizandtracksresponsesandtim
ing.
 6. Thestudentsubmitsthequizuponcompletionorwhentime
 expires.
 7. Thesystemcalculatesthescore,evaluatesperformancean
alytics,andprovidesimmediatefeedback.
 8. TheLLM+RAGsystemgeneratesAI-basedexplanationsfor
 incorrectanswersandactivatestheDoubtSolvingfeature.
 9. Thestudentreviewsanswers,engageswithAIexplanations,
 andclearsdoubtsinteractively.
 10. Thesystemupdates thestudentsperformancemetricsand
 logsteacherreviewoptionsifapplicable.
 24
2.1 Use Case Diagram and Extended Use Cases
 Alternative Flows
 • A1: Quiz Timeout– If the allotted time expires, the system auto-submits
 the quiz with the responses recorded so far.
 • A2: Doubt Solving Unavailable– AtStep8, if the AI Doubt Solving service is temporar
ily unavailable, the system notifies the student and al
lows post-quiz follow-up later.
 • A3: Teacher Review Deferred– Ifthe teacher does not immediately review student per
formance, the system still records analytics for later
 review.
 Table 2.5: Use Case 5: Attempt Quizzes (with Performance
 Analytics and Doubt Solving)
 25
2.ProjectRequirements
 2.2.2.4 UseCase6:ManageUniversityApplications(withLocationTrackingandCom
parison)
 UseCaseID UC-06
 UseCaseName ManageUniversityApplications
 Scope ParhaiPartner
 Actor(s) Student(primary),Counsellor(secondary),System(tertiary)
 Description Thisusecaseallowsastudent tocreate, track, andmanageuni
versityapplications.Thesystemprovidescomparisontools,appli
cationtracking, andlocation-basedrecommendations. Counsel
lorscanreviewandcommentonstudentapplications tosupport
 decision-making.
 Preconditions
 • Thestudentisauthenticatedwithaverifiedaccount
 •Universitydatabaseandcomparisondataareavailable
 • Forcounsellor-guidedapplications,thestudentmusthavean
 assignedcounsellor
 • Forlocation-basedfeatures,deviceorbrowserlocationser
vicesareenabled
 Postconditions
 •Applicationrecordsarestoredandtrackedinthesystem
 •Applicationstatusandprogressareupdatedautomatically
 •Counsellorfeedback(ifapplicable)isrecordedandaccessi
bletothestudent
 •Counsellorsarenotifiedofnewlyaddedorupdatedapplica
tions
 •Keyapplicationdeadlinesarereflectedinthestudentscal
endar
 26
2.1UseCaseDiagramandExtendedUseCases
 Main Success Sce
nario(BasicFlow) 1. The student requests access to theuniversityapplication
 managementfeature.
 2. Thesystemverifiesifthestudenthasanassignedcounsellor.
 3. Ifacounsellorisassigned, thesystemenablescollaborative
 reviewandfeedbackoptions.
 4. Thestudentinitiatesanewuniversityapplicationprocess.
 5. Thesystemprovidessearchandfilteringcapabilitiestoiden
tifysuitableuniversitiesandprograms.
 6. Thestudentexploresandcomparesuniversitiesbasedoncri
teriasuchasranking,admissionrate,andlocationetc.
 7. Thestudentselectsapreferreduniversityandspecifiespro
gramdetails.
 8. The student submits thepreliminaryapplication informa
tion.
 9. The system records the application with an initial In
 Progressstatus.
 10. Ifacounsellorisassigned,thecounsellorgainsaccesstothe
 studentsapplicationdata.
 11. Thecounsellor reviews theapplicationandprovides feed
backorpersonalizedguidance.
 12. Thestudentreviewsthecounsellorsfeedbackandmakesany
 necessaryupdates.
 13. Thesystemupdatestheapplicationstatusandlogsallrevi
sionsfortracking.
 27
2. Project Requirements
 Alternative Flows
 • A1: University Data Unavailable– At Step 5, if complete university data cannot be re
trieved, the system displays partial data and marks
 missing attributes for later update.
 • A2: Location Service Failure– At Step 6, if the system cannot access location data,
 it prompts the student to enter their preferred region
 manually.
 Table 2.6: Use Case 6: Manage University Applications
 (with Location Tracking and Comparison)
 28
2.1UseCaseDiagramandExtendedUseCases
 2.2.2.5 UseCase7:BuildAdmissionDocuments(withDocumentUploading)
 UseCaseID UC-07
 UseCaseName BuildAdmissionDocuments
 Scope ParhaiPartner
 Actor(s) Student(primary),LLM+RAGSystem(secondary)
 Description Thisusecaseenablesastudent toprepareadmission-relateddoc
umentssuchaspersonalstatements,essays,andrecommendation
 letterrequests. ThesystemprovidesAI-assisteddraftingthrough
 theLLM+RAGmodule, customizable templates, anddocument
 uploadingfunctionalityforsupportingmaterials.
 Preconditions
 • Thestudentisauthenticatedwithinthesystem
 • Thestudentsprofilecontainsnecessaryacademicandper
sonalinformation
 •Document templatefortheselectedtypeisavailableinthe
 system
 • Thefileuploadserviceisactiveandoperational
 Postconditions
 • Thecompleteddocumentisgeneratedandstoredinthestu
dentsdocumentlibrary
 • Thedocument islinkedtothecorrespondinguniversityap
plicationrecord
 • Ifacounsellorisassigned,thedocumentissharedforreview
 andfeedback
 • Thefinalizeddocumentbecomesavailablefordownloador
 submission
 29
2.ProjectRequirements
 Main Success Sce
nario(BasicFlow) 1. Thestudentrequeststocreateanewadmissiondocument.
 2. Thesystempromptsthestudenttoselectthedocumenttype
 (e.g., Personal Statement, Essay, RecommendationLetter
 Request).
 3. Thesystemprovidestheappropriatedocumenttemplateand
 guidingquestionstocapturebackgrounddetails,goals,and
 motivations.
 4. Thestudentprovidesresponsestotheguidingquestions.
 5. ThesystemusestheLLM+RAGenginetogenerateadraft
 versionofthedocumentusingtheprovidedinput.
 6. Thesystempresentsthegenerateddraftforreview.
 7. Thestudentreviewsthedraftandrevisesorrefinesthecon
tentasneeded.
 8. Thestudentmayinitiateaplagiarismcheck.
 9. Ifinitiated, thesystemanalyzesthedocumentandprovides
 asimilarityreportwithkeyhighlights.
 10. The student reviews the report, makes any necessary
 changes,andconfirmsthefinalversion.
 11. Thesystemsavesanduploadsthefinalizeddocumenttothe
 studentsdocumentrepository.
 12. Ifthestudenthasanassignedcounsellor,thesystemnotifies
 thecounsellorandsharesthedocumentforreview.
 30
2.1 Use Case Diagram and Extended Use Cases
 Alternative Flows
 • A1: File Upload Failure– AtStep11, if the document upload fails due to file size
 limits, the system suggests compression or splitting the
 f
 ile.
 • A2: Unsupported File Format– At Step 11, if the file format is unsupported, the sys
tem displays acceptable file types and requests resub
mission.
 Table 2.7: Use Case 7: Build Admission Documents (with
 Document Uploading)
 31
2.ProjectRequirements
 2.2.3 Teacher-SpecificUseCases
 2.2.3.1 UseCase8:ManageGeneratedLearningContent
 UseCaseID UC-08
 UseCaseName ValidateandManageGeneratedLearningContent
 Scope ParhaiPartner
 Actor(s) Teacher(primary),LLM+RAGSystem(contentgenerator)
 Description TeachervalidatesAI-generatedlearningmaterialstoensurequal
ity, accuracy, andcurriculumalignment. Notesaresent to the
 teacherbystudentsforvalidation,whilequizzesaregeneratedand
 validateddirectlybytheteachertoexpandandrefinetheirquestion
 bank.
 Preconditions
 • Theteacherisauthenticatedinthesystem
 • Student-submittednotesareavailableforvalidation
 • Teacherssubjectassociationsaredefined
 • TheLLM+RAGcontentgenerationmoduleisoperational
 Postconditions
 •Validatednotesaremarkedasapprovedorrejectedandfeed
backissharedwiththestudent.
 •Approvedquizquestionsarestoredinorupdatedwithinthe
 teachersquestionbank.
 32
2.1UseCaseDiagramandExtendedUseCases
 Main Success Sce
nario(BasicFlow) 1. The teacher requestsaccess topendinglearningmaterials
 forvalidation.
 2. Systemdisplaystwocontentcategories:
 • Student-SubmittedNotes(pendingvalidation)
 •Teacher-GeneratedQuestions
 3. ForStudent-SubmittedNotes:
 (a) Theteacherselectsapendingnoteforevaluation.
 (b) Systemdisplaysthenotecontentalongwithmetadata
 (student,subject,topic,creationdate).
 (c) Teacherreviewsthenotefor:
 •Accuracyandfactualcorrectness
 •Clarityandorganization
 •Relevancetothetopicandcurriculum
 (d) Teachermaymakeinlinecommentsoredits.
 (e) Teacherprovidesfeedbackandchoosesoneofthefol
lowingactions:
 •Approve noteisacceptedandvisibletothestu
dent.
 •Rejectnoteisrejectedandstudentisnotifiedwith
 feedback.
 •RequestRevisionnoteisreturnedforstudentre
vision.
 (f) Systemrecords teachersdecisionandsendsnotifica
tiontothestudent.
 33
2.ProjectRequirements
 4. ForTeacher-GeneratedQuizzesandQuestions:
 (a) Theteacherinitiatesquizquestiongenerationbyspec
ifyingtopic,subject,difficulty,andquantity.
 (b) SystemusesLLM+RAGtogeneratedraftquestions.
 (c) Teacher reviews eachquestion for accuracy, clarity,
 andrelevance.
 (d) Teachervalidatesquestionsbyapproving, editing,or
 rejectingthem.
 (e)Approvedquestionsarestoredintheteachersquestion
 bank.
 5. Systemlogs all validationactivities andupdates teachers
 performancemetrics.
 AlternativeFlows
 •A1:ContentRetrievalFailure Ifacontent itemfails to
 load, thesystemlogstheerrorandcontinueswithavailable
 items.
 •A2: ValidationSaveError If savingfeedbackfails, the
 systemrespondswithanerror.
 •A3:QuestionBankServiceUnavailable If thequestion
 bankserviceisoffline,approveditemsarecacheduntilsyn
chronizationsucceeds.
 Table2.8:UseCase8:ManageGeneratedLearningContent
 34
2.1UseCaseDiagramandExtendedUseCases
 2.2.4 Counsellor-SpecificUseCases
 2.2.4.1 UseCase9:ValidateAdmissionDocuments
 UseCaseID UC-09
 UseCaseName ValidateApplicationDocuments
 Scope ParhaiPartner
 Actor(s) Counsellor(primary)
 Description Thisusecasedescribeshowacounsellor reviewsandvalidates
 student-createdapplicationdocuments (personal statements, es
says,LORs)forquality,content, formatting,andappropriateness
 beforesubmission.
 Preconditions
 • Thecounsellorisauthenticatedinthesystem
 • Thestudenthassubmittedoneormoredocumentsforvali
dation
 • Submitteddocumentsarestoredinsupportedandaccessible
 formats
 Postconditions
 • Eachdocumentreceivesavalidationstatus(approved,revi
sionrequested,orrejected)
 • Feedbackandcommentsarecommunicatedtothestudent
 •Approveddocumentsaremarkedassubmission-readyand
 linkedtocorrespondingapplications
 35
2. Project Requirements
 Main Success Sce
nario (Basic Flow)
 1. The counsellor requests access to documents pending vali
dation.
 2. The system provides a list of student-submitted documents,
 organized by student and document type.
 3. The counsellor selects a document to review.
 4. The system retrieves and presents the document with asso
ciated metadata (student name, program, submission date).
 5. The counsellor evaluates the document based on:
 • Content quality and relevance
 • Grammar and language
 • Structure and organization
 • Formatting and presentation
 • Word count compliance
 • Authenticity and originality
 6. Counsellor provides overall comments and specific feed
back.
 7. The counsellor rates the document across evaluation criteria
 (e.g., clarity, coherence, suitability).
 8. The counsellor selects validation decision:
 • Approve (ready for submission)
 • Approve with minor suggestions
 • Request revision (with specific feedback)
 • Reject (requires major rewrite)
 9. The system records the validation decision, attaches feed
back, and notifies the student.
 10. Approved documents are marked as submission-ready and
 linked to relevant university applications.
 36
2.1 Use Case Diagram and Extended Use Cases
 Alternate Flows
 • A1: Document Retrieval Failure If a document cannot be
 accessed, the system logs the issue and notifies the counsel
lor.
 • A2: Document Revision Before Review If a student up
dates the document before validation, the system refreshes
 the queue with the latest version.
 Table 2.9: Use Case 9: Validate Application Documents