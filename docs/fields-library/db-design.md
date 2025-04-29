## 📘 Custom Field & Form Library - Database Schema Documentation

---

### 📋 `#__fields`

Stores field information with the field type and other extra information

| Column             | Type                          | Description                               |
| ------------------ | ----------------------------- | ----------------------------------------- |
| `fieldId`          | uuid (PK)                     | Primary key, unique field identifier      |
| `context`          | character varying             | Context of the field usage                |
| `groupId`          | character varying             | Grouping ID for fields                    |
| `name`             | character varying             | Field machine-readable name               |
| `label`            | character varying             | Field display label                       |
| `defaultValue`     | character varying             | Default value for the field               |
| `type`             | character varying             | Field type (text, number, dropdown, etc.) |
| `description`      | text                          | Field description                         |
| `state`            | text                          | Field state information                   |
| `required`         | boolean                       | Whether the field is mandatory            |
| `ordering`         | integer                       | Field ordering in form                    |
| `onlyUseInSubform` | boolean                       | If true, only used in subforms            |
| `tenantId`         | uuid (FK)                     | Associated tenant                         |
| `contextId`        | uuid                          | Associated context ID                     |
| `contextType`      | character varying             | Type of context (e.g., 'user')            |
| `fieldParams`      | jsonb                         | Parameters for field rendering            |
| `assetId`          | character varying             | Associated asset ID                       |
| `note`             | character varying             | Additional notes                          |
| `metadata`         | character varying             | Metadata for field                        |
| `access`           | character varying             | Access control details                    |
| `render`           | character varying             | Render control settings                   |
| `fieldAttributes`  | json                          | Additional field attributes               |
| `sourceDetails`    | jsonb                         | Field source details (e.g., API, static)  |
| `dependsOn`        | character varying             | Field dependency on other fields          |
| `maxLength`        | bigint                        | Maximum character length                  |
| `minLength`        | bigint                        | Minimum character length                  |
| `createdAt`        | timestamp with time zone      | Record creation timestamp                 |
| `updatedAt`        | timestamp with time zone      | Record update timestamp                   |
| `createdBy`        | uuid                          | Created by user ID                        |
| `updatedBy`        | uuid                          | Updated by user ID                        |

---

### 📋 `#__FieldValues`

Stores actual submitted values for different fields against specific entities.

| Column             | Type                    | Description                                       |
| ------------------ | ----------------------- | ------------------------------------------------- |
| `fieldValuesId`    | uuid (PK)               | Primary key, unique field value identifier        |
| `fieldId`          | uuid (FK)               | Reference to the field definition                 |
| `itemId`           | uuid                    | ID of the associated entity (user, event, etc.)   |
| `textValue`        | text                    | Value for text fields                             |
| `numberValue`      | numeric                 | Value for number fields                           |
| `dateValue`        | date                    | Value for date fields                             |
| `dropdownValue`    | text                    | Value for dropdown fields                         |
| `radioValue`       | text                    | Value for radio fields                            |
| `checkboxValue`    | text                    | Value for checkbox fields                         |
| `textareaValue`    | text                    | Value for textarea fields                         |
| `fileValue`        | text                    | Value for file fields                             |
| `multiselectValue` | jsonb                   | Value for multiselect fields                      |
| `createdAt`        | timestamp with time zone| Record creation timestamp                         |
| `updatedAt`        | timestamp with time zone| Record update timestamp                           |
| `createdBy`        | uuid                    | Created by user ID                                |
| `updatedBy`        | uuid                    | Updated by user ID                                |

---

### 📋 `#__Forms`

Stores form structures with metadata.

| Column             | Type                     | Description                           |
| ------------------ | ------------------------ | --------------------------------------|
| `formid`           | uuid (PK)                | Primary key, unique form identifier   |
| `title`            | character varying(255)   | Title of the form                     |
| `context`          | character varying(255)   | Context information                   |
| `contextType`      | character varying(50)    | Context type (e.g., 'user', 'event')  |
| `fields`           | jsonb                    | JSON structure of field references    |
| `tenantId`         | uuid (FK)                | Associated tenant                     |
| `createdat`        | timestamp with time zone | Record creation timestamp             |
| `updatedat`        | timestamp with time zone | Record update timestamp               |
| `createdBy`        | uuid                     | Created by user ID                    |
| `updatedBy`        | uuid                     | Updated by user ID                    |
