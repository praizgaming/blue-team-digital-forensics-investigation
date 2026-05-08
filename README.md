#  Digital Forensics Investigation — R v Banks (CR2025-001)

> A digital forensics investigation conducted as part of the HND unit **J7E4 48 Digital Forensics**. This project involved performing a full forensic examination of a suspect's hard drive in a simulated criminal case involving a phishing attack, a fraudulent banking website, and the theft of victims' sensitive financial data.

---

##  Overview

**Case Summary — R v Banks**
A suspect, Robin Banks, was accused of creating a fake banking website to harvest sensitive financial data from victims via phishing emails. A victim, Mrs Ima Scammed, reported that her bank account funds were stolen after she followed a link in a suspicious email to what she believed was her bank's official website.

**Investigator:** Praise Oguns
**Case Number:** CR2025-001
**Date of Investigation:** 25th March 2026

**My task:** Conduct a full forensic examination of the suspect's confiscated hard drive, identify and document all relevant artefacts, reconstruct the timeline of events, and produce a court-admissible forensic report.

**Context:** HND Individual Assessment — Digital Forensics unit
> *Screenshots sourced from original coursework submission.*

---

##  Tools & Technologies Used

| Tool | Vendor | Version | Purpose |
|------|--------|---------|---------|
| FTK Imager | Exterro | 4.7.1.2 | Forensic imaging of the evidence drive |
| Autopsy | Sleuth Kit Labs | 4.21.0 | File system analysis, artefact extraction, timeline generation |
| DB Browser for SQLite | — | 3.13.1 | Examining Microsoft Edge browser history database |
| Write Blocker (Software) | — | — | Preventing any writes to the original evidence drive during imaging |

---

##  Forensic Process Overview

```
Evidence Received
      │
      ▼
Write Blocker Applied (no changes to original drive)
      │
      ▼
Forensic Image Created (FTK Imager)
      │
      ▼
Hash Verification — MD5 & SHA1 crossmatched
(confirmed image is exact, unaltered copy)
      │
      ▼
Analysis Conducted on Image Only (Autopsy)
(original drive sealed in tamper-proof bag)
      │
      ▼
Artefacts Identified & Tagged
      │
      ▼
Timeline Reconstructed
      │
      ▼
Court-Admissible Report Produced
```

---

##  Evidence Details

| Item | Detail |
|------|--------|
| Evidence Label | R-Banks-1-1 |
| Device Type | Hard Disk Drive |
| Vendor | Seagate Technology (Seagate Barracuda) |
| Model | ST40DM001 |
| Serial Number | W1F0RHEE1 |
| Capacity | 40,959 MB |
| Hostname | WIN-FLF6IT69960 |
| IP Address | 209.35.93.101 |
| MAC Address | 00-15-5D-00-53-49 |
| OS | Windows Server 2025 |

---

##  Forensically Safe Environment

- Evidence drive stored in a **Faraday cage** in a locked, access-controlled room
- **Write blocker** applied before imaging to prevent any modification to the original evidence
- All analysis conducted **exclusively on the forensic image** — original drive never touched after seizure
- **Chain of custody** maintained throughout — full log of every transfer, access, and storage event
- Authorisation to investigate granted by **Inspector James Bond**
- MD5 and SHA1 hashes generated and verified to confirm image integrity

---

##  Chain of Custody

| # | Date | Time | Action | Released By | Received By |
|---|------|------|--------|------------|------------|
| 1 | 24 Mar 2026 | 15:00 | Evidence seized from suspect's home, sealed in antistatic bag | Barry Allen (CSI) | David Young (Evidence Storage) |
| 2 | 25 Mar 2026 | 13:45 | Evidence drive handed to forensic investigator | David Young | Praise Oguns (Investigator) |
| 3 | 3 Apr 2026 | 15:45 | Evidence returned to storage after imaging | Praise Oguns | David Young |

---

##  Artefacts Identified

### Artefact 1 — Fraudulent Banking Website (index.html)
- Found in the IIS web server root directory (`inetpub`) on the suspect's machine
- Confirmed **IIS (Internet Information Services)** was installed and actively used
- The `index.html` file contained an **exact replica** of the Vertex Bank website matching the screenshot provided by the victim
- Confirms the suspect deliberately hosted a fraudulent banking website locally on his machine

### Artefact 2 — Victim Data Text File (userdata.txt)
- Found in the same IIS root directory
- Contained harvested sensitive data including bank details, security numbers, phone numbers, emails, and passwords
- **Mrs Ima Scammed's data was present** in this file
- Multiple other victims' data was also found — confirming this was not an isolated attack
- Data was collected via a **PHP script** that submitted user input directly into the text file on the server

### Artefact 3 — Personal Files Linking Device to Suspect
- Documents folder contained personal files including holiday plans, a journal, tax returns, and work projects
- Establishes that **Robin Banks was the primary user** of this machine
- Links the device and all evidence found on it directly to the suspect

### Artefact 4 — Web Developer Job Application (Cover Letter)
- A cover letter for a web developer position was found in the documents folder
- Robin Banks described himself as having **relevant technical skills in website development**
- Removes any claim that the suspect lacked the technical ability to create and host the fraudulent website

### Artefact 5 — Browser History (Hacking Forums)
- Microsoft Edge browser history database extracted from:
`Users\<Administrator>\AppData\Local\Microsoft\Edge\User Data\Default`
- Examined using **DB Browser for SQLite**
- Revealed the suspect **regularly visited hacking websites and forums**
- Demonstrates knowledge of and interest in hacking — supports conclusion that actions were deliberate

### Artefact 6 — Localhost URL in Browser History
- Browser history contained a URL referencing **127.0.0.1** (loopback/localhost address)
- Confirms the suspect was **running and testing the fraudulent website locally on his own machine**
- When victims entered data into the fake site, it was submitted directly to the locally hosted server and captured by the PHP script

### Artefact 7 — Phishing Email Template (Recovered from Deleted Files)
- A **Microsoft Word document was recovered from the deleted files** of the suspect's machine
- Contained a pre-written phishing email template impersonating Vertex Bank
- Used **social engineering tactics** — posing as an urgent account warning requiring immediate action
- Contained a **{Customer_Name} placeholder** — indicating emails were designed to be sent in bulk to multiple victims
- The fact it was deleted suggests the suspect **attempted to destroy evidence** before the device was seized

### Artefact 8 — Python & VS Code Installation
- **Microsoft VS Code** and **Python** were found installed on the machine
- Python is commonly used for scripting and automation
- The `{Customer_Name}` placeholder in the email template is consistent with a **Python script automating bulk personalised phishing emails**
- Further supports that the attack was planned, deliberate, and technically sophisticated

---

##  Reconstructed Timeline of Events

| Date & Time | Event |
|-------------|-------|
| 01/01/2025 — 15:55 | Suspect creates phishing email template in MS Word and saves it |
| 03/01/2025 — 14:00 | Suspect develops fake Vertex Bank website, hosted locally via IIS |
| 05/01/2025 — 09:00 | Suspect sets up MySQL database to store harvested victim data |
| 07/01/2025 — 11:00 | Suspect sends phishing email to victim Mrs Ima Scammed |
| 07/01/2025 — 13:32 | Victim clicks malicious link and submits sensitive data to fake website |
| 07/01/2025 — 13:39 | Victim data recorded and stored in suspect's local database via PHP script |
| 08/01/2025 — 16:00 | Suspect attempts to delete phishing email template from device |
| 10/01/2025 — 09:00 | Device seized by police and handed to evidence storage officer |
| 25/03/2026 — 13:45 | Evidence received by investigator (Praise Oguns) for forensic examination |
| 03/04/2026 — 10:00 | Forensic image acquired using FTK Imager with write blocker applied |
| 29/04/2026 — 15:45 | Analysis conducted in Autopsy — artefacts identified and tagged |

---

##  Legal Framework

The findings support charges against Robin Banks under the following legislation:

| Legislation | Relevance |
|-------------|-----------|
| **Computer Misuse Act 1990** | Unauthorised access to computer systems and creation of tools to facilitate fraud |
| **Data Protection Act 2018** | Obtaining personal data of multiple victims without consent, in breach of privacy rights |

---

## Conclusion

The forensic investigation identified **eight distinct artefacts** on Robin Banks' hard drive that together establish a clear, deliberate, and technically sophisticated phishing scheme. Key findings include:

- A fraudulent Vertex Bank website hosted locally on IIS, matching the victim's screenshot
- A text file containing the personal and financial data of Mrs Ima Scammed and multiple other victims
- A phishing email template recovered from deleted files — showing attempted evidence destruction
- Browser history confirming active interest in hacking and local testing of the fraudulent site
- Personal files conclusively linking the device to Robin Banks
- Evidence of Python automation consistent with bulk phishing email distribution

These findings support criminal prosecution and referral to relevant authorities.

---

##  Key Takeaways

- Gained practical experience performing a full digital forensics investigation from evidence intake to court-ready report
- Understood the importance of chain of custody and forensically safe environments in ensuring evidence is admissible
- Used industry-standard tools — FTK Imager and Autopsy — used by real digital forensics professionals
- Learned how to extract and analyse browser history databases using DB Browser for SQLite
- Understood how deleted files can be recovered and used as evidence
- Developed skills in reconstructing a timeline of events from digital artefacts
- Understood the legal framework (Computer Misuse Act, Data Protection Act) that governs digital forensics in the UK

---


## Screenshots
<img width="663" height="202" alt="Image" src="https://github.com/user-attachments/assets/3cb706bb-ac42-435b-bf59-8e987c9a09b8" />
Fig1. Write Blocker Activated <br />

<img width="591" height="321" alt="Image" src="https://github.com/user-attachments/assets/ea31fb77-847b-48fa-a35a-80deb86e91b5" />
Fig2. Phishing email template <br />

<img width="615" height="347" alt="Image" src="https://github.com/user-attachments/assets/ade8a8cd-e79e-471c-84cf-aa0f0ba94352" />
Fig3.HTML file of bank website <br />
 
<img width="696" height="473" alt="Image" src="https://github.com/user-attachments/assets/aa219e4d-2bfd-4b41-87dc-3c113a93c4f4" />
Fig4.PHP script used to harvest victim data <br />
 
<img width="645" height="387" alt="Image" src="https://github.com/user-attachments/assets/feab8c90-312c-4317-a171-157415aff074" />
Fig5.Victim sensitive data <br />

<img width="390" height="440" alt="Image" src="https://github.com/user-attachments/assets/ef29a7f9-c821-48fb-9415-18792624cc77" />
Fig6.Holiday Plans of suspect <br />

<img width="752" height="135" alt="Image" src="https://github.com/user-attachments/assets/caf86668-4e9b-435f-8f59-66aec4beb0ad" />
Fig7.Web developer job application by suspect <br />
 
<img width="692" height="532" alt="Image" src="https://github.com/user-attachments/assets/ad339fa0-7157-43fc-a986-46ea68e6abc6" />
Fig8.MS Edge History found 
Fig9.Browser History shows suspicious website visits <br />

<img width="656" height="235" alt="Image" src="https://github.com/user-attachments/assets/21c319ea-2e6b-4ed3-a43d-02d1bf8754aa" />
Fig10.Phishing email template file recovered from recycle bin <br />
 
## 📁 Project Structure

```
blue-team-digital-forensics-investigation/
│
├── README.md                    ← You are here
├── chainofcustody

```

---

*Completed as an individual assessment for the HND unit J7E4 48 Digital Forensics.*
*Case: R v Banks — CR2025-001. Simulated criminal investigation environment.*
