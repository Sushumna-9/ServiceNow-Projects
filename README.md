# ServiceNow-Projects
**Streamlining Ticket Assignment for Efficient Support Operations Project**

#User Creation Steps
- Open ServiceNow and navigate to "All" > "Users" under "System Security".
- Click "New" and enter User ID, First Name, Last Name, Email then submit.
- Example users:
  - manne.niranjan (Manne Niranjan)
  - katherine.perice (Katherine Perice)
#Group Creation Steps
- Go to "All" > "Groups" under "System Security".
- Click "New" and enter targeted group details.
- Example groups: Certificates, Platform.
#Role Creation and Assignment
- Go to "All" > "Roles" under "System Security" and click "New" to define required roles.
- Assign users to corresponding groups and roles under "Tables" and "Group Members":
  - Katherine Pierce → Certificates Group → Certificationrole
  - Manne Niranjan → Platform Group → Platformrole
#Table Creation
- Navigate to "All" > "Tables" under "System Definition" and click "New".
- Name table: Operations related.
- Add columns and create modules as needed.
#Assigning Roles to Table Permissions
- For table 'operations related', set Application Access:
  - Needs platform & certificate roles for read/write permissions.
  - Use "Elevate role" as security admin for editing.
#Creating ACL (Access Control List)
- Go to "All" > "ACL" under "System Security" and create new ACLs for key fields.
- Example requires: 'admin' role for specific record operations and fields:
  - Write field: uoperationsrelated.utickectraiseddate, uname, uissue, uservicerequestno
#Flow Designer: Ticket Assignment Automation
- Open "Flow Designer" under "Process Automation".
- Create Flows for ticket auto-assignment:
  - "Regarding Certificate" flow triggered by specific issue text routes to Certificates group.
    - Table: Operations related, Field: issue, Operator: is, Value: Regarding Certificates → Assign to Certificates group
  - "Regarding Platform" flow triggered by login/platform errors routes to Platform group.
    - Table: Operations related, Field: issue, Operator: is, Value: Unable to login to platform/404 Error/User expired → Assign to Platform group
- Save and activate each Flow.

