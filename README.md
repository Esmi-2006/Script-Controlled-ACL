# Script-Controlled-ACL
In this milestone we have to create Users and Roles as per the requirement
# ServiceNow Script-Controlled ACL Security Implementation

## Project Overview
This project implements a **script-controlled Access Control List (ACL)** framework within **ServiceNow** to enforce robust, conditional record-level security. The primary objective is to restrict data visibility and modifications based on user roles and specific record field values, ensuring that sensitive data remains isolated and protected across all platform forms, lists, and Service Portal interfaces.

By leveraging advanced script conditions alongside standard data filters, the configuration establishes granular control over the entire CRUD (Create, Read, Update, Delete) lifecycle for custom table records.

## Key Features & Architecture

* **Custom Schema Design:** Created a dedicated data repository table (`u_institution_details`) featuring specialized reference tracking, choice lists, and auto-numbering mechanisms.
* **Role-Based Provisioning:** Developed a segmented hierarchy of custom security roles (`bb1`, `bb2`, `bb3`, `bb4`) assigned to targeted test users to model organizational divisions.
* **Advanced Read ACL:** Integrated a combination of a static data filter (`Branch IS EEE`) and an elevated JavaScript script to conditionally permit only specific branch members or platform administrators to view contextual records.
* **Dynamic Lifecycle Operations:** Enforced distinct operation boundaries across the rest of the application lifecycle by configuring tailored operational rules:
  * **Create Operations:** Regulated explicitly via the `bb2` role assignment.
  * **Write/Edit Operations:** Bound explicitly to the `bb3` role definition.
  * **Delete Operations:** Restricted directly to the high-clearance `bb4` role.
* **System Impersonation Testing:** Formally verified security boundary enforcement through comprehensive administrator and target user impersonation drills.

## Implementation Framework Diagram
* **Data Context:** `u_institution_details` (Institution Details Table)
* **Target Isolation Condition:** Records where `Branch == 'EEE'`
* **Security Matrix Realization:**
  * **Admin:** Full Overriding Access (Read/Write/Create/Delete).
  * **User + bb1:** Allowed to **Read** EEE branch records only.
  * **User + bb1 + bb2:** Allowed to **Read** and **Create** EEE records.
  * **User + bb1 + bb2 + bb3:** Allowed to **Read**, **Create**, and **Edit** EEE records.
  * **User + bb1 + bb2 + bb3 + bb4:** Full Lifecycle **CRUD** operational capability on EEE records.
  * **Unauthorized Users:** Complete access denial across the target schema.

***
 Google Drive Link :[https://drive.google.com/drive/folders/18VoK6DXVDb789OXmqeWnvf-OSZ8F_XMM?usp=drive_link]
 
