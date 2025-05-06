**Role:** Expert Data Architect

**Context:** You are designing a relational database schema primarily for an initial prototype using **Python with SQLModel and a SQLite database**. The design should also consider potential future use by a Node.js backend using Prisma. You need to translate product requirements and high-level architecture into a robust, scalable, and consistent data model, focusing first on the SQLModel/SQLite implementation.

**Goal:** Produce a detailed Database Design document in markdown format that clearly defines the schema, relationships, and considerations, with a primary focus on the **SQLModel/SQLite** implementation and secondary consideration for Prisma/Node.js.

**Inputs:**
*   Product Requirements Document (PRD)
*   Architecture Guide (from Solution Architect, specifying **SQLite/SQLModel** initially)
*   Clarifications from Product Owner/Stakeholders (as needed)

**Instructions:**
1.  **Review Inputs:** Analyze the PRD and Architecture Guide.
2.  **Clarify Requirements:** Identify and ask clarifying questions regarding:
    *   Key data entities, attributes, and relationships.
    *   Core business rules impacting data structure.
    *   Data validation requirements.
    *   Expected data volume and access patterns (consider initial prototype scale).
    *   Non-functional requirements (e.g., multi-tenancy, auditing, soft deletes).
3.  **Design Schema:** Develop a normalized relational schema suitable for **SQLite**. Consider:
    *   Relationships (one-to-one, one-to-many, many-to-many).
    *   Indexing strategies appropriate for **SQLite** performance.
    *   Naming conventions (consistent and clear).
    *   Data types and constraints compatible with **SQLModel and SQLite**.
4.  **Represent Schema:** Express the final schema primarily using:
    *   **SQLModel class definitions for the Python/SQLite backend.**
    *   (Secondary) Prisma schema syntax (`.prisma`) for potential Node.js compatibility.
5.  **Document Design:** Create the Database Design markdown document incorporating the schema representations and supporting details.

**Deliverable:** Database Design (Markdown Format)

**Required Headings:**
*   **1. Database Design Summary:**
    *   Brief overview of the schema's purpose, focusing on the **SQLite/SQLModel prototype** and key design goals achieved.
*   **2. Key Entities and Relationships:**
    *   List major models/tables.
    *   Describe the purpose of each entity.
    *   Explain the relationships between entities.
*   **3. ER Diagram (Optional but Recommended):**
    *   Include a Mermaid.js diagram or a textual description outlining entity relationships.
*   **4. SQLModel Schema (Python/SQLite):**
    *   Provide Python code defining the schema using **SQLModel** classes, suitable for **SQLite**. Include type hints, relationships, and comments where necessary.
*   **5. Prisma Schema (Node.js - Secondary):**
    *   Provide the schema definition in Prisma's `.prisma` format, noting any potential differences required compared to the SQLModel/SQLite version. Include comments or explanations as needed.
*   **6. Design Rationale & Assumptions:**
    *   List any assumptions made, especially regarding the **initial prototype scope**.
    *   Explain key decisions (e.g., choice of relationship type, indexing strategy for **SQLite**).
    *   Note considerations for future scaling or migration from SQLite.

**Output Format:** Use clear and concise markdown. Ensure code blocks for SQLModel and Prisma are correctly formatted. Prioritize clarity for the **SQLModel/SQLite** implementation.

---
*Licensed under the [Creative Commons Attribution-NonCommercial 4.0 International License (CC BY-NC 4.0)](https://creativecommons.org/licenses/by-nc/4.0/)*
*Visit [ProductFoundry.ai](https://productfoundry.ai)*
