Summary,Description,Issue Type,Acceptance Criteria,Sprint,Labels
Spike: ICMP API for File Upload (Prospect Metadata Focus),"As a developer, I want to identify and test the required metadata for uploading files to ICMP for a prospect, and determine what metadata needs updating when a prospect is converted to a customer, so that file uploads and updates are handled correctly.",Story,"- All required and recommended metadata fields for a prospect file upload to ICMP are identified and documented (e.g., prospect ID, name, status).
- A test file is successfully uploaded to ICMP with prospect-specific metadata.
- Metadata fields that must be updated upon conversion to customer are identified and documented.
- The metadata of a test file in ICMP is successfully updated to reflect conversion.
- Automated tests are created for file upload and metadata update scenarios, if feasible.
- Test catalog is updated for each acceptance criteria.",Spike Sprint,prospect-support
Spike: CRM API for Prospect Details,"As a developer, I want to identify and test the CRM APIs that provide prospect details, so that we can retrieve all necessary information for document space creation and invite logic.",Story,"- All relevant CRM API endpoints for retrieving prospect details are identified and documented.
- Data fields returned by each endpoint are listed, highlighting those required for document space creation and invite logic.
- Prospect details are successfully retrieved using the identified APIs in a test environment.
- Authentication requirements, request/response formats, and any limitations or gaps are documented.
- Recommendations for any additional data or API enhancements are provided.
- Automated tests are created for CRM API retrieval scenarios, if feasible.
- Test catalog is updated for each acceptance criteria.",Spike Sprint,prospect-support
Spike: ACT360 HH Contact ID API for Prospect Members,"As a developer, I want to check and validate the ACT360 HH contact ID API to ensure it supports retrieving all members of a prospect household, so that we can correctly display and manage household members for prospects.",Story,"- The ACT360 HH contact ID API is identified and its documentation reviewed.
- A test call is made to the API using a prospect HH context, and the response is validated.
- All relevant data fields for household members are documented.
- Any limitations or gaps in supporting prospect households are identified and documented.
- Automated tests are created for the API call, if feasible.
- Test catalog is updated for each acceptance criteria.",Spike Sprint,prospect-support
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
- Test catalog is updated for each acceptance criteria.",Sprint 1,prospect-support
CRM Integration to Check Prospect Availability,"As an advisor, I want the system to verify a prospect’s existence and fetch their details from the CRM, so I can ensure the correct person is being onboarded.",Story,"- The system can query the CRM using prospect identifiers.
- If the prospect exists, their details are retrieved; if not, an error is returned.
- All new code is covered by unit tests with at least 80% coverage.
- Integration tests are created to verify CRM queries.
- Automated end-to-end tests are implemented for CRM integration.
- Test catalog is updated for each acceptance criteria.",Sprint 1,prospect-support
Upload a File to Prospect Space (Advisor-Initiated),"As an advisor, I want to upload files to a prospect’s document space, so I can share important documents with them.",Story,"- I can upload one or more files to the prospect’s document space.
- The prospect receives a notification when a new file is uploaded.
- All new code is covered by unit tests with at least 80% coverage.
- Integration tests are created to verify file upload and notification logic.
- Automated end-to-end tests are implemented for the upload and notification flow.
- Test catalog is updated for each acceptance criteria.",Sprint 2,prospect-support
List Document Requests from Prospect Page (Advisor View),"As an advisor, I want to view all document requests for a prospect using their ECN or prospect ID, so I can track outstanding and completed requests.",Story,"- I can retrieve document requests using ECN or prospect ID.
- The list displays request status, due dates, and related files.
- All new code is covered by unit tests with at least 80% coverage.
- Integration tests are created to verify document request retrieval.
- Automated end-to-end tests are implemented for the document request listing.
- Test catalog is updated for each acceptance criteria.",Sprint 2,prospect-support
Edit Preferences on Prospect Space,"As an advisor, I want to edit notification settings and access permissions for a prospect’s document space, so I can tailor the experience to the prospect’s needs.",Story,"- I can update notification preferences for the prospect.
- I can manage access permissions (e.g., add/remove team members).
- Changes are saved and reflected immediately.
- All new code is covered by unit tests with at least 80% coverage.
- Integration tests are created to verify preference and permission updates.
- Automated end-to-end tests are implemented for editing preferences.
- Test catalog is updated for each acceptance criteria.",Sprint 2,prospect-support
Send Invite to Prospect (with Branching Logic),"As an advisor, I want the system to send the invite to the correct system (ANG or DSF) based on the prospect’s ECN and online access status, so the prospect receives the right type of access.",Story,"- If the prospect has an ECN and online access, the invite is sent via ANG.
- If the prospect does not have an ECN, or has an ECN without online access, the invite is sent via DSF.
- The system logs which system the invite was sent through.
- The invite contains a secure link to the document space.
- The system tracks invite status (sent, accepted, expired).
- All new code is covered by unit tests with at least 80% coverage.
- Integration tests are created to verify invite logic and system integration.
- Automated end-to-end tests are implemented for the invite flow.
- Test catalog is updated for each acceptance criteria.",Sprint 3,prospect-support
Revoke Prospect Access Upon Conversion,"As an advisor, I want a prospect’s access to the prospect portal revoked when they are converted to a customer, so they can no longer use the prospect portal.",Story,"- When a prospect’s status changes to customer in the CRM, their access code for the prospect portal is revoked via the DSF system.
- The prospect receives a notification that their access has changed.
- The document space is no longer accessible via the prospect portal.
- All new code is covered by unit tests with at least 80% coverage.
- Integration tests are created to verify access revocation.
- Automated end-to-end tests are implemented for the access revocation flow.
- Test catalog is updated for each acceptance criteria.",Sprint 4,prospect-support
Batch Process to Detect Prospect Conversion and Revoke Access,"As a developer, I want to run a scheduled batch job that checks if any prospects have been converted to customers in the CRM, so that I can trigger access revocation and rerouting actions automatically.",Story,"- The batch job runs at a configurable interval (e.g., hourly, daily).
- The job queries the CRM for prospects whose status has changed to customer since the last run.
- For each converted prospect, the DSF system is called to revoke their prospect portal access code.
- Any necessary notifications or rerouting flags are set for the user.
- The batch job logs all actions and errors for monitoring and audit purposes.
- All new code is covered by unit tests with at least 80% coverage.
- Integration tests are created to verify batch processing and DSF integration.
- Automated end-to-end tests are implemented for the batch conversion and access revocation flows.
- Test catalog is updated for each acceptance criteria.",Sprint 4,prospect-support
Update ICMP Metadata with Customer Information Upon Conversion,"As a developer, I want to update the ICMP metadata of all files uploaded to a prospect’s document space with the customer’s information when the prospect is converted, so that all files are correctly associated with the customer record.",Story,"- When a prospect is converted to a customer, the system retrieves all files uploaded to the prospect’s document space.
- For each file, the system updates the ICMP metadata to include the new customer information (e.g., customer ID, name, status).
- The update is performed via the ICMP API, and any errors are logged.
- The process is idempotent and does not duplicate metadata updates.
- A summary of updated files and any failures is logged for audit and troubleshooting.
- All new code is covered by unit tests with at least 80% coverage.
- Integration tests are created to verify metadata update logic.
- Automated end-to-end tests are implemented for the metadata update flow.
- Test catalog is updated for each acceptance criteria.",Sprint 5,prospect-support
Reroute to Client Portal After Conversion,"As a customer, I want to be automatically redirected to the client portal if I try to access my old prospect portal link after conversion, so I can continue managing my documents as a customer.",Story,"- If a converted customer tries to use their old prospect portal link, they are redirected to the client portal login page.
- A message explains that their access has changed due to their new customer status.
- All new code is covered by unit tests with at least 80% coverage.
- Integration tests are created to verify rerouting logic.
- Automated end-to-end tests are implemented for the rerouting flow.
- Test catalog is updated for each acceptance criteria.",Sprint 5,prospect-support
Call DSF System to Revoke Login Access Code,"As a developer, I want to call the DSF system to revoke a prospect’s login access code when they are converted to a customer, so their prospect portal access is securely disabled.",Story,"- The system detects when a prospect is converted to a customer.
- An API call is made to the DSF system to revoke the access code.
- The revocation is logged for audit purposes.
- All new code is covered by unit tests with at least 80% coverage.
- Integration tests are created to verify DSF API calls.
- Automated end-to-end tests are implemented for the access code revocation flow.
- Test catalog is updated for each acceptance criteria.",Sprint 5,prospect-support
List My Document Requests (API/Portal),"As a customer or prospect, I want to use an API or portal to view all my outstanding and completed document requests, so I can easily track what is required of me and what I have already submitted.",Story,"- I can retrieve my document requests via a secure API endpoint or portal, using my authenticated session or unique identifier.
- The API/portal returns all outstanding and completed document requests, including status, due dates, and any related files or upload links.
- The response is paginated and includes all necessary metadata for the customer/prospect to act on requests.
- All new code is covered by unit tests with at least 80% coverage.
- Integration tests are created to verify API/portal request/response and security.
- Automated end-to-end tests are implemented for the customer/prospect document request API/portal.
- Test catalog is updated for each acceptance criteria.",Sprint 5,prospect-support
Upload a File to My Document Space (Customer/Prospect-Initiated),"As a prospect or customer, I want to upload a file to my document space in response to a document request, so I can securely provide the required documents to my advisor.",Story,"- I can upload one or more files to my document space via the web portal or API.
- The uploaded file(s) are securely saved and associated with the correct document request and my profile.
- The advisor is notified when I upload a file.
- I receive confirmation that my file was successfully uploaded.
- All new code is covered by unit tests with at least 80% coverage.
- Integration tests are created to verify file upload, storage, and notification logic.
- Automated end-to-end tests are implemented for the file upload flow.
- Test catalog is updated for each acceptance criteria.",Sprint 5,prospect-support
Final UAT, Documentation, Go-Live Prep,"As a product owner, I want to ensure all features are tested, documented, and ready for production, so the release is smooth and successful.",Story,"- All UAT feedback is addressed.
- Documentation is finalized and accessible.
- Go-live checklist is complete.
- All test cases are up to date in the test catalog.
- Test catalog is updated for each acceptance criteria.",UAT/Finalization,prospect-support
