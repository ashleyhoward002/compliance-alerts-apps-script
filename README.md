# compliance-alerts-apps-script

# 📧 Compliance Deadline Alert System

A Google Apps Script automation that sends email reminders when staff certifications are about to expire. Built for healthcare compliance tracking at Michigan Medicine.

## 🎯 Problem

Manually tracking 35+ staff certifications = missed deadlines, compliance risks, and administrative burden.

## ✅ Solution

Automated email alerts that:
- Send **weekly reminders** at 28, 21, and 14 days before expiration
- Escalate to **daily alerts** during the final 7 days
- Continue **daily notifications** for expired certifications
- Send **supervisor summaries** with action items

## 📊 Features

| Feature | Description |
|---------|-------------|
| 🔔 Smart Alerts | Weekly → daily escalation based on urgency |
| 📧 Auto-Emails | Sends to staff and supervisors automatically |
| 🎨 Color-Coded Rows | Visual status indicators in the spreadsheet |
| 📋 Custom Menu | One-click actions in Google Sheets |
| ⏰ Daily Trigger | Runs automatically every morning |

## 🚀 Quick Start

### 1. Create the Google Sheet

Create a new Google Sheet with a tab named `Staff Data` and these columns:

| Staff Name | Email | Certification | Expiration Date |
|------------|-------|---------------|-----------------|
| John Smith | john@example.com | BLS | 2026-04-15 |

### 2. Add the Script

1. In Google Sheets: **Extensions → Apps Script**
2. Delete the default code
3. Paste the contents of `compliance-alerts.gs`
4. Click **Save**

### 3. Authorize & Test

1. Select `testScript` from the function dropdown
2. Click **Run**
3. Authorize when prompted
4. Check **View → Logs** for results

### 4. Set Up Daily Automation

1. Click the **clock icon** (Triggers)
2. Click **+ Add Trigger**
3. Configure:
   - Function: `sendSupervisorSummary`
   - Event source: Time-driven
   - Type: Day timer
   - Time: 8:00 AM - 9:00 AM
4. Save

## 📁 Files

```
compliance-alerts-apps-script/
├── README.md
├── compliance-alerts.gs    # Main script
└── screenshots/
    ├── sheet-example.png
    ├── script-editor.png
    └── trigger-setup.png
```

## 🔧 Configuration

### Enable Real Emails

Uncomment these lines in the script:

```javascript
// In sendAlert():
GmailApp.sendEmail(email, subject, body);

// In sendSupervisorSummary():
GmailApp.sendEmail(supervisorEmail, subject, body);
```

### Change Supervisor Email

Update this line in `sendSupervisorSummary()`:

```javascript
const supervisorEmail = 'your-supervisor@example.com';
```

## 📈 Alert Schedule

| Days Until Expiry | Alert Type | Frequency |
|-------------------|------------|-----------|
| 28 days | 📋 Reminder | Once |
| 21 days | 📋 Reminder | Once |
| 14 days | ⏰ Warning | Once |
| 7 days or less | ⚠️ Urgent | Daily |
| Expired | 🚨 Expired | Daily |

## 🎨 Color Coding

The `colorCodeRows()` function applies these colors:

| Status | Color | Hex |
|--------|-------|-----|
| Expired | Red | #ffcccb |
| Urgent (≤7 days) | Orange | #ffebcc |
| Warning (≤14 days) | Yellow | #ffffcc |
| Reminder (≤30 days) | Light Blue | #e6f3ff |
| OK (>30 days) | Green | #ccffcc |

## 🏥 Use Case

Built for the **Department of Orthopaedic Surgery at Michigan Medicine** to track:
- BLS/ACLS certifications
- Medical licenses
- DEA registrations
- Board certifications
- Mandatory training completions

## 💡 Customization Ideas

- Add Slack notifications via webhook
- Create a dashboard with charts
- Track notification history
- Add "Last Notified" column to prevent spam
- Export compliance reports to PDF

## 🛠️ Tech Stack

- **Google Apps Script** - Automation platform
- **SpreadsheetApp** - Google Sheets integration
- **GmailApp** - Email automation
- **Time-based Triggers** - Scheduled execution

## 👩‍💻 Author

**Ashley Howard**  
Administrative Assistant Senior | AI/ML Developer  
Michigan Medicine - Department of Orthopaedic Surgery

- GitHub: [@ashleyhoward002](https://github.com/ashleyhoward002)
- LinkedIn: [linkedin.com/in/ashleyhoward-data](https://linkedin.com/in/ashleyhoward-data)

## 📄 License

MIT License - Feel free to use and modify for your organization!


---

*Built with ☕ and Google Apps Script*
