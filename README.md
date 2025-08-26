 Event Management System - Database Design

 
A comprehensive event management database built with Supabase & PostgreSQL


 Overview:


This database is designed to support a scalable event management system that enables users to create events, manage RSVPs, and handle attendee data efficiently. The schema prioritizes data integrity, performance, and extensibility—making it suitable for real-world applications.

## 🔗 Project Links

| Resource | Link | Description |
|----------|------|-------------|
| **GitHub Repository** | [event-app.git](https://github.com/karthikampolu/event-app.git) | Complete source code with Next.js frontend |
| **Live Deployment** | [Vercel App](https://event-app-psi.vercel.app/login) | Production deployment (Bonus feature) |





**Key Features:**

User registration and management

Event creation and organization

 RSVP tracking with status management

 Full referential integrity

 Audit trails with timestamps

 Scalable design for future enhancements

**Database Architecture :**


Entity Relationship Model
Core Entities
Entity	Purpose	Key Relationships
Users	User registry and authentication	One-to-many with Events (creators)
Events	Event details and metadata	Many-to-many with Users (via RSVPs)
RSVPs	Junction table for event attendance	Links Users ↔ Events


** Design Choices & Rationale :**

**1. Normalized Structure :**


Choice: Full 3NF normalization

Rationale: Eliminates data redundancy, ensures consistency, and prevents update anomalies

Trade-off: Slightly more complex queries for better data integrity

**2. Primary Key Strategy :**


Choice: Auto-incrementing integer IDs for all entities

Rationale: Ensures uniqueness, optimal for indexing, and provides consistent join performance

Implementation: PostgreSQL sequences (nextval())


**3. Foreign Key Constraints :**

Choice: Strict referential integrity enforcement

Rationale: Prevents orphaned records and maintains data consistency

**Implementation:**

sql


events.created_by → users.id


rsvps.user_id → users.id  


rsvps.event_id → events.id


**4. Timestamp Strategy:**


Choice: created_at and updated_at on all tables

Rationale: Enables audit trails, change tracking, and debugging

Default: Automatic timestamp with now() function

**5. RSVP Status Design:**


Choice: Custom enum type for RSVP status

Rationale: Ensures data consistency, prevents invalid states

Values: 'yes', 'no', 'maybe' (extensible)


**Technical Implementation:**


Database Platform

Engine: PostgreSQL 17.4.1

Hosting: Supabase Cloud

**Project ID**: zjwsyupnkawcmxmqsdue


**Key Features Implemented**


 ACID Compliance - Full transaction support

 Referential Integrity - Foreign key constraints

 Data Validation - Custom types and constraints

 Performance - Proper indexing on foreign keys

 Scalability - Normalized structure supports growth
