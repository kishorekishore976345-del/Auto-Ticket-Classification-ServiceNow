# Auto Ticket Classification using Flow Designer

## 📌 Project Overview

The **Auto Ticket Classification using Flow Designer** project is a ServiceNow solution designed to automate the classification of common school IT helpdesk tickets using **Flow Designer**.

When a new Incident Workflow record is created, the automation checks the Short Description. Based on the configured keywords, it automatically updates the Category and Subcategory and generates a confirmation email for the caller.

This reduces repetitive manual classification, supports consistent ticket categorisation, and provides a confirmation message after ticket submission.

## 🎯 Project Objectives

- Create a custom Incident Workflow table to store school IT support tickets.
- Automatically classify common IT issues based on the Short Description.
- Populate the appropriate Category and Subcategory.
- Reduce manual intervention in ticket classification.
- Generate a confirmation email for the caller.
- Provide a workflow that can be maintained and extended in ServiceNow.

## 🛠️ Platform & Technology

- **Platform:** ServiceNow
- **Automation Tool:** Flow Designer
- **Business Area:** School IT Helpdesk / Incident Management
- **Custom Table:** Incident Workflow
- **Flow Name:** Auto Classify School IT Tickets
- **Notification:** Send Email action

## 🔄 Project Workflow

```text
Caller / Helpdesk User
        ↓
Incident Workflow Form
        ↓
Create Ticket
        ↓
Flow Designer Trigger
(Record Created)
        ↓
Check Category is Empty
        ↓
Check Short Description Keywords
        ↓
Update Category & Subcategory
        ↓
Send Confirmation Email
        ↓
Verify Ticket and Email
```

## ⚙️ Flow Designer Configuration

The project uses a Flow named **“Auto Classify School IT Tickets”**.

### Trigger

- **Trigger:** Record Created
- **Table:** Incident Workflow
- **Entry Condition:** Category is Empty

### Classification Configuration

| **Short Description Condition** | **Category** | **Subcategory** |
| -------------------------------- | ------------ | --------------- |
| Contains “Wi-Fi” or “Network” | Network | Wi-Fi |
| Contains “Projector” | Hardware | Projector |
| Contains “Forgot password” | Access | Forgot Password |
| Contains “Slow Computer” | Performance | Slow Computer |

### Email Configuration

| **Field** | **Value** |
| --------- | --------- |
| Action | Send Email |
| To | Caller → Email |
| Subject | Your Request for the issue has been submitted |
| Body | Ticket confirmation message |

## 🧩 Implementation

The solution was implemented in ServiceNow using a custom **Incident Workflow** table and Flow Designer.

The table includes fields for Number, Caller, Category, Subcategory, Short Description, Description, State, Assigned Group, and Assigned to. The Subcategory field is configured to depend on Category.

The Flow Designer automation is configured to run when a record is created and Category is empty. It checks the Short Description, updates the matching Category and Subcategory, and then performs the configured email action.

## 🧪 Testing

The project testing covered the following scenarios:

1. **Wi-Fi / Network:** Short Description — “WiFi not working in library”; expected Category — Network; Subcategory — Wi-Fi.
2. **Projector:** Short Description — “Projector not turning on”; expected Category — Hardware; Subcategory — Projector.
3. **Forgot Password:** Expected Category — Access; Subcategory — Forgot Password.
4. **Slow Computer:** Expected Category — Performance; Subcategory — Slow Computer.
5. **Email verification:** A generated email record and its preview were inspected in ServiceNow.

The email record/preview confirms that the notification was generated in the instance. External mailbox delivery was not independently confirmed.

## 📸 Project Evidence

Add the actual screenshots from your ServiceNow project to this repository to demonstrate:

- Incident Workflow custom table and fields
- Subcategory dependency configuration
- Flow Designer trigger and entry condition
- Classification branches and Update Record actions
- Send Email action configuration
- Test records showing the category and subcategory results
- Generated email record and preview
- Project Update Set marked Complete and XML export

> Only use genuine screenshots captured from your ServiceNow instance as project evidence. Any illustrative mockups should be clearly labelled as mockups.

## 🎥 Project Demonstration

The project demonstration can show the complete workflow:

```text
Create Incident Workflow Ticket
        ↓
Enter Short Description
        ↓
Save the Record
        ↓
Flow Designer Classifies the Ticket
        ↓
Category and Subcategory are Updated
        ↓
Confirmation Email is Generated
        ↓
Verify the Result
```

For the Wi-Fi test, enter **“WiFi not working in library”** and verify that the Category is **Network** and the Subcategory is **Wi-Fi**.

## 📦 Deployment Artifact

The **Project Update Set** was marked Complete and exported as an XML file. The XML contains the exported ServiceNow configuration changes and should be retained as the project deployment artifact.

Do not include instance passwords, access tokens, or other credentials in this repository.

## 👥 Team

**Project:** Auto Ticket Classification using Flow Designer  
**Team members:** Add the actual team member names here.

## ✅ Conclusion

The project demonstrates how ServiceNow Flow Designer can automate classification of common school IT helpdesk tickets. When a supported ticket is created, the flow checks its Short Description, updates the Category and Subcategory, and generates a confirmation email for the caller.

The solution reduces repetitive manual classification and provides a consistent workflow for the four configured issue types. The exported Update Set XML is retained as the configuration artifact.
