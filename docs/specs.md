Product Requirements Document: Rose - The Flexible UK Home Support Connector (MVP) - Supabase Edition


1. Executive Summary


Rose aims to solve the problem of finding flexible, affordable, and trusted non-medical home support that falls outside the scope of CQC-regulated activities. The MVP will connect families seeking companionship, household help, personal assistance, and light, clearly defined non-medical personal care, with vetted, self-employed carers. The core objective of this MVP is to prove the viability of a "trust-first" marketplace model by facilitating seamless discovery, booking, and simulated payment for these non-regulated services in a specific UK region.


2. User Roles & Critical Actions (MVP)


The MVP will support two primary user roles:


User Role 1: Individual Carers


Single Most Critical Action: A Carer must be able to successfully receive and manage a booking request from a Family, leading to a completed and simulated paid-for service.


User Role 2: Families


Single Most Critical Action: A Family must be able to discover, book, and successfully receive a service from a vetted Carer that meets their specific non-CQC needs and fosters a sense of trust.


3. User Journeys (High-Level Flows)


3.1. Family's Journey: From Arrival to First Booking


Arrival & Initial Understanding: Family lands on the platform, immediately grasping Rose's core offering as a hyper-local, trusted connector for non-CQC regulated home support.


Location & Pre-defined Service Selection: Family enters their postcode/location and selects specific non-CQC service types from a pre-defined list.


Browse Vetted Carer Profiles (Trust Building Phase 1 - No Registration Required): Family views a curated list of available Carers matching criteria, seeing profile photo, name, rate, services, and prominent trust indicators (DBS, references, intro video).


Deep Dive into Carer Profiles (Trust Building Phase 2 - No Registration Required): Family explores detailed carer profiles including personal intro video, comprehensive bio, full list of services, verified references, availability calendar, and insurance partnership information.


Initiate Contact / Request a Service (Registration / Login Prompt): Upon clicking "Message Carer" or "Request Booking," Family is prompted to sign up/log in if not already. Supabase Authentication handles this process.


Compose Message / Submit Booking Request (Post-Registration): After login, Family can send a direct message or submit a booking request, specifying dates, times, and pre-defined services.


Carer Review & Confirmation: The selected Carer reviews and accepts/declines/proposes an alternative for the request.


Payment Setup & Booking Confirmation (Simulated): Family is prompted to add/confirm test payment method details. The booking is formally confirmed, and simulated payment terms are communicated.


Service Delivery & Post-Service Actions: Carer delivers service. Platform internally generates a simulated sales invoice. Family is prompted to submit a review for the Carer.


3.2. Carer's Journey: From Initial Interest to Service Completion & Payment


Initial Interest & Platform Discovery: Carer discovers Rose and understands its value as an introducer for non-CQC home support.


Expression of Interest & Initial Application: Carer starts the registration process, providing basic contact info and confirming self-employed status. Supabase Authentication handles this.


Comprehensive Vetting & Trust Infrastructure Onboarding: Carer undergoes multi-step process:


Initiates/provides proof of Enhanced DBS.


Provides professional references for verification.


Completes detailed public profile (photo, bio, intro video).


Selects specific non-CQC services from Rose's pre-defined list.


Defines geographical coverage using an interactive map tool.


Sets hourly rates.


Confirms engagement with third-party liability insurance partner.


(MVP: Likely manual review and approval by Rose team).


Availability Setup: Once approved and their profile is live, Carer sets up their availability calendar.


Receiving & Managing Booking Requests: Carer receives booking requests/messages via the Rose platform (notifications) with full details.


Accepting / Declining / Communicating with Families: Carer can accept, decline, propose alternatives, or message the Family directly through the platform.


Service Delivery: Carer delivers the agreed-upon non-CQC home support service.


Confirmation of Service & Invoicing (Automated via Utility Stack): Carer marks job as complete, inputs actual duration. Platform's utility stack automatically generates a simulated invoice from Carer to Family.


Payment Receipt (Simulated): Carer's internal platform balance is updated (simulated payment received minus simulated commission).


Review Management & Profile Building: Carer receives feedback/reviews from families, building their reputation.


4. Functional Requirements (MVP)


4.1. User Authentication & Profile Management


For All User Roles:


User Registration: Email/password signup with email verification via Supabase Authentication.


User Login: Email/password login via Supabase Authentication.


Password Management: "Forgot Password" / Password Reset via Supabase Authentication, Change Password.


Basic Account Settings: Email address update.


Notifications: Essential transactional email notifications (leveraging Supabase's email capabilities or integrated service).


Specific to Families:


Family Profile Creation & Management: Ability to input/edit basic contact details, add/manage primary service address(es), securely add/manage test credit/debit card details (using test mode gateway).


Communication & Messaging: In-platform secure direct messaging with Carers.


Specific to Individual Carers:


Carer Public Profile Creation & Management: Ability to input/edit contact details, upload profile photo (to Supabase Storage), upload intro video (to Supabase Storage or via URL), select services from fixed list, define geographical coverage (interactive map), set hourly rates.


Vetting Status Display: System display/indicator for Enhanced DBS, Reference, and Insurance verification status.


Availability Management: Intuitive calendar interface to set and update availability.


Financial Details Management: Secure input of test bank account details for simulated payouts.


Communication & Messaging: In-platform secure direct messaging with Families.


4.2. Carer Discovery (Search & Filtering)


Search & Filtering:


Location-Based Search: Postcode/address input with filtering based on carer's defined geographical coverage.


Service Type Filtering: Multi-select from pre-defined non-CQC service list (with clear definitions).


Availability Filtering: Date & Time selection (showing carer's available slots).


Optional for MVP: "Open Now" filter, Rate filtering.


Carer Profile Display (Search Results & Detail View):


Search Results List View: Concise card with photo, name, snippet, rate, distance, and prominent trust indicators (DBS, References, Video, Star Rating), top services.


Detailed Carer Profile View: Comprehensive bio, embedded intro video player (from Supabase Storage or external URL), full service list, read-only availability calendar, detailed trust elements (DBS, References, Insurance, Trust Circles), Reviews & Ratings.


Call to Actions: "Message Carer" and "Request Booking" buttons (triggering registration/login if not logged in).


User Experience & Sorting:


Sorting Options: Relevance (default), Distance, Rate, Rating.


Clear Call to Action: Prominent buttons to initiate contact or booking.


No Results/Refine Search: Clear guidance if no carers match criteria.


4.3. Booking Request & In-Platform Messaging


Family Initiating a Booking Request / Message:


"Request Booking" Flow: Clear button on Carer Profile, service selection, date/time picker (showing carer's availability), duration input, optional brief notes, summary screen for review.


"Message Carer" Flow: Clear button on Carer Profile, initial message composer, initiates new private conversation thread.


Carer Receiving & Responding to Booking Requests:


Booking Request Notification: Dashboard alert, email notification.


"Manage Request" Interface: View request details (Family, services, date/time, estimated earnings, notes), clear actions to Accept/Decline/Message Family.


Optional for MVP: Propose Alternative.


Booking Status Updates: Automated notifications for acceptance/declining.


In-Platform Messaging System (Between Family & Carer):


Dedicated Messaging Inbox: Threaded conversations, unread indicators.


Message Composer: Standard text input.


Message Display: Chronological order, sender/recipient identification, timestamp.


Notifications for New Messages: Dashboard alert, configurable email alerts.


Security & Privacy: Private threads, no automatic exposure of personal contact info.


4.4. Payments & Invoicing (MVP - Simulated/Test Mode)


A. Family Payment Setup & Authorization (Simulation):


Secure Payment Method Input UI: Use a payment gateway's (e.g., Stripe's) test mode to provide a secure UI for Families to input test credit/debit card details.


Add/Manage Test Payment Methods: Families can "add" these test cards to their profile and select a default. No real charges occur.


Consent for Automated "Charges": Families explicitly agree that their stored test payment method would be charged automatically upon service completion.


Simulated Pre-authorization: Display message indicating a pre-authorization would be placed, no actual hold.


B. Post-Service Payment Processing (Internal Logic & Display):


Service Completion & Time Confirmation: Carer marks a service as "Completed" on the platform, inputs actual duration.


Internal Calculation of "Charge": The platform's backend calculates the full gross service amount.


Simulated "Charge" Record: An internal record is created indicating a simulated charge to the Family.


Payment Status & Notifications (Simulated): System defaults to "payment successful" or can simulate failure; notifications sent accordingly.


C. Invoicing & Commission Management (Display Only):


Automated Sales Invoice Generation (Carer to Family - Display): Generate a display-only sales invoice from Carer to Family for gross amount. Access for Families.


Automated Sales Invoice Generation (Rose to Carer - Commission - Display): Internally calculate commission; generate display-only sales invoice from Rose to Carer for this amount. Access for Carers.


D. Carer Payouts & Balance Management (Internal Logic & Display):


Carer Bank Account Input (Test Data): Carers input test bank account details.


Internal Carer Account Balance Simulation: Gross funds "deposited," commission "deducted," net balance "available" internally.


Simulated Periodic Payouts: System has a scheduled "payout" event (e.g., "Weekly Payout Day") where the internal balance is "transferred" visually. No real bank transfer.


Carer Earnings Dashboard & Statements (Display Only): Dashboard showing simulated balance, earnings, commissions, payouts; downloadable simulated statements.


4.5. Admin & Moderation


Admin Dashboard & User Management:


A secure, dedicated web-based dashboard accessible only to authorized Rose staff.


Search and view user accounts (Family & Carer).


Enable/Disable/Suspend user accounts, GDPR-compliant account deletion process.


Basic messaging to individual users for account issues/disputes.


Carer Vetting & Onboarding Management:


Dedicated section for reviewing new Carer applications (view details, docs, questionnaire).


Approve/Reject application workflow with feedback.


Status tracking for DBS & Reference verification (manual input for MVP).


Control display of "Verified" badges on public profiles.


Activity Monitoring & Content Moderation:


Monitor all booking and simulated payment statuses.


User reporting mechanism for inappropriate messages/users.


Admin access to reported messages for review.


Review and moderation of user-generated content (bios, videos, reviews).


Dispute Resolution:


Formal dispute reporting mechanism for users.


Dedicated admin interface to view/manage disputes (assign, view related data).


Ability for admins to communicate directly with parties within a dispute.


Tools to document resolution steps and outcomes.


5. Non-Functional Requirements (MVP)


5.1. Security & Privacy


Data Encryption: All data in transit (HTTPS/TLS 1.2+), sensitive data at rest encryption (handled by Supabase's managed PostgreSQL).


Authentication & Session Management: Strong password policies (hashing/salting, handled by Supabase Auth), secure session management (tokens, timeouts, handled by Supabase Auth), brute-force protection (handled by Supabase Auth).


Authorization & Access Control: Role-Based Access Control (RBAC) and Principle of Least Privilege for all user and admin roles (leveraging Supabase Row Level Security (RLS) for data access).


Application Security: Basic OWASP Top 10 protections (Injection, Broken Auth, Sensitive Data Exposure).


Security Logging & Monitoring: Basic logging of security-relevant events (leveraging Supabase logs).


Third-Party Integrations Security: Reliance on PCI-DSS compliant payment gateway (Stripe) and secure DBS integration.


Privacy (GDPR-Compliant by Design): Data minimization, explicit consent, comprehensive Privacy Policy, basic user rights (access, rectification, erasure), secure handling of sensitive data (DBS, addresses), defined data retention, basic data breach protocol.


5.2. Performance & Scalability


Performance / Response Times:


Page Load Times: Core pages within 3 seconds, subsequent pages within 2 seconds.


API Response Times: Core data retrieval within 500ms (90%), transactional actions within 1 second (90%).


Search Performance: Carer search results within 2-3 seconds.


Concurrency & Load Handling (MVP Target): Comfortably support 50-100 concurrent active users; handle 200-500 daily active users without degradation (leveraging Supabase's scalability).


Scalability (Architectural Considerations for Future Growth): Cloud-native (GCP), stateless components where possible, scalable database (Supabase managed PostgreSQL), CDN for static assets, modular design.


Availability: 99% uptime target during core operational hours (leveraging Supabase's high availability). Robust error handling, graceful degradation for third-party outages, automated daily backups (handled by Supabase).


Monitoring & Analytics: Basic system and user journey performance monitoring (leveraging Supabase monitoring tools and custom integrations).


5.3. User Experience (UX) & Usability


General: Intuitive navigation, consistent layout, clean/uncluttered UI, readable typography, clear feedback/error messages, basic accessibility (semantic HTML, keyboard navigation, contrast), full mobile responsiveness.


Trust-First Elements: Prominent visual badges for vetting, easily accessible Intro Videos, visible reviews, explicit non-CQC messaging, clear fixed service definitions, clear payment security assurances (HTTPS, Stripe branding).


Family-Specific: Intuitive search flow, visual carer cards, effective filtering, clear CTAs, guided booking forms, streamlined messaging.


Carer-Specific: Streamlined onboarding with progress indicators, clear guidance for profile creation (bios, videos, services), intuitive interactive map for coverage, easy-to-use availability calendar, efficient job/finance dashboard, one-click job completion, transparent earnings display.


6. Technical Architecture & Technology Stack (MVP Recommendation)


Backend-as-a-Service (BaaS): Supabase (Managed PostgreSQL, Authentication, Storage, Edge Functions for some logic)


Backend (API & Business Logic - for custom logic): Python with Django (for complex business logic, custom APIs not directly handled by Supabase, and Admin UI)


Frontend (User Interface): React (with Next.js)


Payment Gateway Integration: Stripe (in test mode for MVP)


Messaging/Notifications: Third-party email service (e.g., SendGrid, Mailgun)


Content Delivery Network (CDN): GCP Cloud CDN (for Next.js static assets)



