# Rose MVP Development Plan

This is a structured, step-by-step task breakdown to implement the "Rose - The Flexible UK Home Support Connector" MVP based on the provided PRD. All tasks are listed with unique IDs, dependencies, and descriptions.

---

## 1. Project Initialization & Setup

### 1.1 Project Infrastructure

- [ ] **1.1.1**: Initialize Git repository and create core branches (`main`, `dev`)  
  _Dependencies: None_

- [ ] **1.1.2**: Setup project documentation folder with README, CONTRIBUTING, and CODEOWNERS  
  _Dependencies: 1.1.1_

- [ ] **1.1.3**: Create project management board (e.g., GitHub Projects, Linear, Jira) with columns for Backlog, In Progress, Review, Done  
  _Dependencies: 1.1.1_

### 1.2 Tech Stack Bootstrapping

- [ ] **1.2.1**: Initialize Supabase project and configure PostgreSQL, Auth, Storage  
  _Dependencies: 1.1.1_

- [ ] **1.2.2**: Bootstrap Next.js app with TypeScript and TailwindCSS  
  _Dependencies: 1.1.1_

- [ ] **1.2.3**: Setup backend API service with Django and DRF  
  _Dependencies: 1.1.1_

- [ ] **1.2.4**: Connect frontend to Supabase SDK  
  _Dependencies: 1.2.1, 1.2.2_

---

## 2. Authentication & Authorization

### 2.1 Supabase Auth Integration

- [ ] **2.1.1**: Implement email/password registration and login via Supabase  
  _Dependencies: 1.2.1, 1.2.2, 1.2.4_

- [ ] **2.1.2**: Create user roles in Supabase (Family, Carer, Admin) using custom claims  
  _Dependencies: 2.1.1_

- [ ] **2.1.3**: Implement forgot password and reset functionality  
  _Dependencies: 2.1.1_

- [ ] **2.1.4**: Secure routes based on role using Supabase Row-Level Security (RLS)  
  _Dependencies: 2.1.2_

---

## 3. Core Domain Models & Database Design

- [ ] **3.1.1**: Define schema for Family, Carer, Booking, Message, Payment, Review in Supabase/Postgres  
  _Dependencies: 1.2.1_

- [ ] **3.1.2**: Implement RLS policies to restrict access per user role  
  _Dependencies: 3.1.1, 2.1.2_

---

## 4. Carer Onboarding & Management

### 4.1 Carer Application Flow

- [ ] **4.1.1**: Create carer registration form with photo/video upload, service selection, location map, rates  
  _Dependencies: 2.1.2, 3.1.1_

- [ ] **4.1.2**: Implement DBS/reference/insurance verification status indicators  
  _Dependencies: 4.1.1_

- [ ] **4.1.3**: Admin dashboard for reviewing/verifying carer onboarding  
  _Dependencies: 4.1.2, 3.1.1_

---

## 5. Family Booking Experience

### 5.1 Search & Discovery

- [ ] **5.1.1**: Implement search UI with filters: location, service type, availability  
  _Dependencies: 2.1.2, 3.1.1_

- [ ] **5.1.2**: Display results as carer cards with trust indicators  
  _Dependencies: 5.1.1_

- [ ] **5.1.3**: Create detailed carer profile view  
  _Dependencies: 5.1.2_

### 5.2 Booking Flow

- [ ] **5.2.1**: Implement booking request form with pre-filled availability  
  _Dependencies: 5.1.3_

- [ ] **5.2.2**: Enable carers to accept, decline, or message family  
  _Dependencies: 5.2.1_

- [ ] **5.2.3**: Simulate booking confirmation & notify both parties  
  _Dependencies: 5.2.2_

---

## 6. Messaging System

- [ ] **6.1.1**: Build private message threads between carer and family  
  _Dependencies: 2.1.1, 3.1.1_

- [ ] **6.1.2**: Add notification system for new messages  
  _Dependencies: 6.1.1_

---

## 7. Simulated Payments & Invoicing

- [ ] **7.1.1**: Implement test-mode payment method setup using Stripe  
  _Dependencies: 3.1.1_

- [ ] **7.1.2**: Simulate payment flow and display internal balance updates  
  _Dependencies: 7.1.1, 5.2.3_

- [ ] **7.1.3**: Auto-generate invoices and payout summaries  
  _Dependencies: 7.1.2_

---

## 8. Admin Tools & Moderation

- [ ] **8.1.1**: Build admin interface for user management, vetting status, and content moderation  
  _Dependencies: 4.1.3, 6.1.1_

- [ ] **8.1.2**: Add reporting tools for inappropriate behavior/messages  
  _Dependencies: 8.1.1_

- [ ] **8.1.3**: Implement GDPR deletion, account disable, and dispute resolution workflows  
  _Dependencies: 8.1.1_

---

## 9. UX, Trust & Accessibility

- [ ] **9.1.1**: Implement visual trust indicators: badges, reviews, intro videos  
  _Dependencies: 4.1.2, 5.1.2_

- [ ] **9.1.2**: Ensure WCAG accessibility compliance, keyboard navigation, contrast ratios  
  _Dependencies: 5.1.1, 5.1.3_

- [ ] **9.1.3**: Make all key flows fully responsive (mobile/tablet/desktop)  
  _Dependencies: All frontend components_

---

## 10. Testing & Launch

- [ ] **10.1.1**: Write unit tests for backend and frontend logic  
  _Dependencies: All feature implementations_

- [ ] **10.1.2**: Perform E2E testing of core user journeys (e.g. booking, messaging, onboarding)  
  _Dependencies: All feature implementations_

- [ ] **10.1.3**: Setup error logging, analytics, and monitoring  
  _Dependencies: 1.2.2, 1.2.3_

- [ ] **10.1.4**: Conduct final UAT and MVP launch checklist  
  _Dependencies: 10.1.1, 10.1.2_

---
