# Dental Care Follow‑Up Workflow for n8n

## Overview
This workflow automates daily patient follow‑up emails for dental treatments using n8n.  
It reads patient data from a Google Sheet, identifies which patients need follow‑ups, sends personalized messages through Gmail, and marks those patients as contacted.

## Key Features
- Automatically triggers once per day through a Schedule Trigger.
- Reads patient information from a Google Sheet.
- Filters patients who:
  - Have not yet received a follow‑up.
  - Had their appointment more than 3 days ago.
- Sends personalized follow‑up emails via Gmail according to treatment type.
- Updates the Google Sheet to mark the follow‑up as sent and records the current date.
- Optional daily summary email indicating how many messages were sent.

## Workflow Structure
```
[Schedule Trigger]
       ↓
[Google Sheets – Get Rows]
       ↓
[Function – Filter Patients Due]
       ↓
[Switch – Treatment Type]
     ↙︎        ↓        ↘︎
 [Set – Cleaning]  [Set – Crown]  [Set – ...]
     ↓                 ↓
     ↘──> [Gmail – Send Email]
                 ↓
      [Google Sheets – Update Row]
```

## Treatment Branches Supported
1. Cleaning (Oral Prophylaxis)  
2. Surgical Extraction  
3. Simple Extraction  
4. Crown Placement  
5. Bridge Placement  
6. Denture Fabrication and Repair  
7. Restoration (Filling)  
8. Post and Core Build‑Up  
9. SRP (Scaling and Root Planing)  
10. Sealant  
11. Fluoride Treatment  
12. Default / Other Procedures

## Setup Instructions
1. Import the `Dental_Care_Follow_UP.json` workflow into n8n.
2. Connect Google credentials for:
   - Google Sheets (read and update).
   - Gmail (send email).
3. Open the Function node and verify column names match your Google Sheet headers.
4. Update each Set node to include practice name, doctor’s name, and desired email signature.
5. Confirm your Google Sheet has columns:
   - Name  
   - Email  
   - Appointment Date  
   - Treatment Details  
   - FollowUp Sent?  
   - Sent Date  
6. Activate the workflow.

## How to Use
- The workflow runs automatically each day at the scheduled time.
- To test manually, click **Execute Workflow** in n8n.
- Check your Gmail “Sent” folder and corresponding updates in your Google Sheet.

## File
- `Dental_Care_Follow_UP.json` – complete exported n8n workflow.

## Contact
Created and maintained by Kye Brathwaite.   
For questions or improvements, open an issue in this repository.

---

Would you like me to include an example **.gitignore** file too (so you don’t accidentally commit system or credential files)?
