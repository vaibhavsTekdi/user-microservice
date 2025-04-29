## 📝 Product Requirements Document (PRD) - Custom Field & Form Library

---

### 📌 Overview
The Custom Field & Form Library enables services to define, render, and manage dynamic forms and custom fields without the need for database schema changes. It provides a reusable and scalable foundation for capturing structured data across different services such as users, cohorts, events, and more.
Field values are saved across multiple columns (e.g., textValue, numberValue, dateValue) to improve query performance, enhance validation, and support better reporting.

---

### 🎯 Objectives
- Allow creation and configuration of form structures consisting of various field types.
- Enable runtime attachment of forms to any service entity (e.g., user, event, cohort) using itemId and entityType.
- Store and retrieve field values submitted via forms across type-specific columns.
- Support integration across services through APIs or npm package.
- Ensure flexibility for frontend rendering and validation via JSON-driven form definitions.

---

### ✅ Features
- Define fields with type, label, validation rules, options, and visibility.
- Compose forms with ordering, grouping, and logic using JSON structures.
- Store submitted field values across multiple typed columns for filtering and reporting.
- APIs to: Fetch forms by entity type, Submit field values, Retrieve submitted values
- Support multiple entity types using itemId and entityType.
- Dynamic configuration with no need for DB schema migration.
- Reusable across all services with minimal setup.
- Designed for integration with role and permission systems.

---

### 📋 Supported Field Types
- text
- number
- date
- dropdown
- radio
- checkbox
- textarea
- file (optional)
- multiselect (optional)

### 🧹 Entities

#### 1. Form
- id, name, description, isEnabled, formType, formJson
- JSON to include field IDs, grouping, ordering

#### 2. Field
- id, name, label, type, validation rules, options (for dropdown/radio), visibility, required

#### 3. Field Value
- id, fieldId, itemId (userId, cohortId, eventId, etc.), entityType (e.g., 'user', 'event'), textValue, numberValue, dateValue, dropdownValue, etc., createdBy, createdAt

---

### 📁 Data Models
Refer to [Custom Field and Form Table Schema Documentation](./db-design.md) for detailed entity structure.

---

### 👥 Assumptions

- itemId will be globally unique for each record (userId, eventId etc.)
- entityType is passed to identify the owning service context
- Permissions will be handled at the API layer or middleware
- No hardcoded logic in consuming services — forms are dynamic