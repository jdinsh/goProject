Summary,Description,Issue Type,Acceptance Criteria,Sprint,Labels,Start Date,Due Date
Spike: ICMP API for File Upload (Prospect Metadata Focus),"As a developer, I want to identify and test the required metadata for uploading files to ICMP for a prospect, and determine what metadata needs updating when a prospect is converted to a customer, so that file uploads and updates are handled correctly.",Story,"- All required and recommended metadata fields for a prospect file upload to ICMP are identified and documented (e.g., prospect ID, name, status).
- A test file is successfully uploaded to ICMP with prospect-specific metadata.
- Metadata fields that must be updated upon conversion to customer are identified and documented.
- The metadata of a test file in ICMP is successfully updated to reflect conversion.
- Automated tests are created for file upload and metadata update scenarios, if feasible.
- Test catalog is updated for each acceptance criteria.",Spike Sprint,prospect-support,2026-09-16,2026-09-29
Spike: CRM API for Prospect Details,"As a developer, I want to identify and test the CRM APIs that provide prospect details, so that we can retrieve all necessary information for document space creation and invite logic.",Story,"- All relevant CRM API endpoints for retrieving prospect details are identified and documented.
- Data fields returned by each endpoint are listed, highlighting those required for document space creation and invite logic.
- Prospect details are successfully retrieved using the identified APIs in a test environment.
- Authentication requirements, request/response formats, and any limitations or gaps are documented.
- Recommendations for any additional data or API enhancements are provided.
- Automated tests are created for CRM API retrieval scenarios, if feasible.
- Test catalog is updated for each acceptance criteria.",Spike Sprint,prospect-support,2026-09-16,2026-09-29
Spike: ACT360 HH Contact ID API for Prospect Members,"As a developer, I want to check and validate the ACT360 HH contact ID API to ensure it supports retrieving all members of a prospect household, so that we can correctly display and manage household members for prospects.",Story,"- The ACT360 HH contact ID API is identified and its documentation reviewed.
- A test call is made to the API using a prospect HH context, and the response is validated.
- All relevant data fields for household members are documented.
- Any limitations or gaps in supporting prospect households are identified and documented.
- Automated tests are created for the API call, if feasible.
- Test catalog is updated for each acceptance criteria.",Spike Sprint,prospect-support,2026-09-16,2026-09-29
Search and Create Document Space for a Prospect,"As an advisor, I want to search for a prospect and create a document space, so I can securely share and manage documents with them.
- The system listens for the incoming HH (Household) context.
- If the incoming context is a prospect, the system tags it as a prospect.
- The system calls the ACT360 HH contact ID API to retrieve the members of the prospect’s household.
- If the FA/CA (Financial Advisor/Client Associate) clicks 'Add Client,' the system creates the document space for the prospect.",Story,"- I can search for a prospect by name, email, or prospect ID.
- The system checks for ECN and online access status.
- The system listens for the incoming HH context and, if it is a prospect, tags it accordingly.
- The system calls the ACT360 HH contact ID API to retrieve household members for the prospect.
- When FA/CA clicks 'Add Client,' a document space is created for the prospect.
- I am notified if the prospect does not exist.
- All new code is covered by unit tests with at least 80% coverage.
- Integration tests are created to verify CRM lookup, ACT360 API integration, and document space creation.
- Automated end-to-end tests are implemented for the full search and create flow.
- Test catalog is updated for each acceptance criteria.",Sprint 1,prospect-support,2026-09-30,2026-10-13
CRM Integration to Check Prospect Availability,"As an advisor, I want the system to verify a prospect’s existence and fetch their details from the CRM, so I can ensure the correct person is being onboarded.",Story,"- The system can query the CRM using prospect identifiers.
- If the prospect exists, their details are retrieved; if not, an error is returned.
- All new code is covered by unit tests with at least 80% coverage.
- Integration tests are created to verify CRM queries.
- Automated end-to-end tests are implemented for CRM integration.
- Test catalog is updated for each acceptance criteria.",Sprint 1,prospect-support,2026-09-30,2026-10-13
Upload a File to Prospect Space (Advisor-Initiated),"As an advisor, I want to upload files to a prospect’s document space, so I can share important documents with them.",Story,"- I can upload one or more files to the prospect’s document space.
- The prospect receives a notification when a new file is uploaded.
- All new code is covered by unit tests with at least 80% coverage.
- Integration tests are created to verify file upload and notification logic.
- Automated end-to-end tests are implemented for the upload and notification flow.
- Test catalog is updated for each acceptance criteria.",Sprint 2,prospect-support,2026-10-14,2026-10-27
List Document Requests from Prospect Page (Advisor View),"As an advisor, I want to view all document requests for a prospect using their ECN or prospect ID, so I can track outstanding and completed requests.",Story,"- I can retrieve document requests using ECN or prospect ID.
- The list displays request status, due dates, and related files.
- All new code is covered by unit tests with at least 80% coverage.
- Integration tests are created to verify document request retrieval.
- Automated end-to-end tests are implemented for the document request listing.
- Test catalog is updated for each acceptance criteria.",Sprint 2,prospect-support,2026-10-14,2026-10-27
Edit Preferences on Prospect Space,"As an advisor, I want to edit notification settings and access permissions for a prospect’s document space, so I can tailor the experience to the prospect’s needs.",Story,"- I can update notification preferences for the prospect.
- I can manage access permissions (e.g., add/remove team members).
- Changes are saved and reflected immediately.
-
