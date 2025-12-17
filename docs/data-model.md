## Data Model Design

### Allocation__c
Represents a single allocation request in the system.

Key fields:
- Allocation_Number__c (Auto Number)
- Status__c (Picklist)
- Priority__c (Picklist)
- Assigned_To__c (Lookup User)

Design Notes:
- Status drives workflow and validations.
- Auto Number provides readable identifiers.

### Allocation_Task__c
Represents tasks associated with an allocation.

Key fields:
- Allocation_c (Lookup to Allocation_c)
- Task_Status__c (Picklist)
- Due_Date__c (Date)

Relationship Choice:
Lookup relationship chosen over Master-Detail to allow
flexibility in task management and avoid unintended cascade deletes.

### Status Flow Rules
- Draft → Submitted
- Submitted → In Progress
- In Progress → Completed (only if all tasks completed)
- Admin can cancel at any stage
