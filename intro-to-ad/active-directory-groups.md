# Introduction to Active Directory

## Active Directory Groups

- group similar users in domain; assign them domain permissions
- active directory built-in and custom group types
- number of groups and combinations of group access can grow exponentialy
  - 1000 users, 100 groups, 1000000 possible combinations

### Organizational Units (OU)

- logical container for users, groups, computers, and other OUs
- can be used to group objects based on location, department, or function
  - apply group policies to specific location, department, or function
- OUs can also be used to delegate administrative tasks to a user, such as  
  resetting passwords or unlocking user accounts without giving them additional  
  admin rights that they may inherit through group membership.
- groups are used for provisioning access to resources, while OUs are used for  
  organizing and managing objects in the directory.

## Types of Groups

- Groups simplify management of permissions and resource assignments
- Used for users, computers, and contact objects
- Provide easier administration than individual assignments
- Examples of resources: printers, file share access
- Benefits:
  - Time-saving for admins
  - Easier to audit access
  - Simpler to modify or revoke permissions
- Process:
  - Create or use existing group
  - Grant group permissions to resource
  - Add users to group
  - Users inherit permissions from group membership
- Flexibility:

  - Can remove users from group without affecting others
  - Permissions for remaining users stay intact

- **Two fundamental characteristics**:

  - Type: Defines the purpose of the group
  - Scope: Shows how the group can be used within the domain or forest

- **Group Type Selection:**
  - Required when creating a new group
  - **Two main types**:
    - Security Groups
    - Distribution Groups

## Security Groups

- **Purpose:** Primarily used to assign permissions and rights to a group of users efficiently.
- **Benefits:**
  - Streamlines the management of user permissions and rights.
  - Reduces administrative overhead compared to individual assignments.
  - All users within a security group automatically inherit the group's assigned permissions.
  - Makes it easier to add or remove users from a group without altering the group's overall permissions.
- **Functionality:**
  - Users added to a security group will have the same access rights to a resource as the group.
  - Simplifies user management by allowing administrators to control access to resources through group membership.

## Distribution Groups

- **Purpose:** Used for email distribution lists.
- **Functionality:**
  - Similar to mailing lists, enabling efficient email communication to a group of users.
  - Applications like Microsoft Exchange leverage distribution groups to send emails to multiple recipients simultaneously.
  - In Microsoft Outlook, distribution groups can be used to auto-populate email addresses in the "To" field.
- **Limitations:**
  - Cannot be used to assign permissions or rights to resources in a domain environment.
  - Primarily intended for email communication and management.

## Group Scopes

- Three types: Domain Local, Global, Universal
- **Domain Local Group:**
  - Manages permissions for resources within its own domain.
  - Can include users from other domains but cannot be used in other domains.
  - Can be nested within other local groups, not global groups.
- **Global Group:**
  - Grants access to resources in other domains.
  - Contains only accounts from its own domain.
  - Can be added to both global and local groups.
- **Universal Group:**
  - Manages resources across multiple domains within the same forest.
  - Can contain users from any domain.
  - Stored in the Global Catalog, changes trigger forest-wide replication.
  - Best practice: maintain global groups as members to minimize replication overhead.
- **Key takeaway:** Group scope selection impacts resource access and management across domains. Consider the location of resources and users when choosing a group scope.

### Changing Group Scopes

- Conversions possible with limitations:
  - Global to Universal: Only if not part of another Global Group.
  - Domain Local to Universal: Only if no nested Domain Local Groups.
  - Universal to Domain Local: No restrictions.
  - Universal to Global: Only if no nested Universal Groups.

## Built-in vs. Custom Groups

- **Built-in Security Groups**
  - Created automatically with a Domain Local Group scope upon domain creation
  - Serve specific administrative purposes
  - Only user accounts can be added, no group nesting allowed
  - Example: Domain Admins (Global security group)
- **Custom Groups**
  - Created by organizations to suit specific needs (security & distribution)
  - Can be triggered by changes/additions to the AD environment (e.g., Exchange installation)
  - Require careful management, especially those with high privileges
- **Key Points:**
  - Built-in groups offer pre-defined administrative roles
  - Custom groups provide flexibility for specific organizational needs
  - Changes to the environment can introduce new groups, demanding attention to security implications

## Nested Group Membership in Active Directory (AD)

- Users can gain privileges indirectly through nested groups (a group being a member of another group).
- This can lead to accidental access rights that are hard to detect.
- Tools like BloodHound help visualize and uncover these complex privilege chains.
- Critical for both security professionals (finding vulnerabilities) and administrators (understanding their AD setup).
