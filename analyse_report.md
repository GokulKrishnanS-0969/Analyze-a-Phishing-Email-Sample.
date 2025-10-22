# Phishing Email Analysis — Task 2
**Sample:** phishing_email_sample.png  
**Analyst:** Gokul Krishnan 
**Date analyzed:** 2025-10-22  

---

## 1. Overview
The email pretends to be from **Adobe Acrobat**, claiming that an MSI Benefits Group document has been shared.  
It urges the recipient to click **“Open”**, leading to a credential-phishing site that mimics Adobe’s login.

---

## 2. Phishing indicators

| # | Indicator | Evidence (from screenshot) | Explanation |
|---|------------|----------------------------|--------------|
| 1 | **Suspicious sender address** | Message comes from `message@adobe.com` but marked *“You don’t often get email from this address”*. | Attackers often spoof the “From” field to appear trusted; Microsoft ATP flags it as abnormal. |
| 2 | **Fake file-sharing alert** | “MSI Benefits Group Invoices and Payment Statement REF-2567…” | Unusual document type/subject; legitimate Adobe Share messages rarely include invoice refs. |
| 3 | **Embedded “Open” button** | Blue *Open* button links externally (hover shows non-Adobe URL). | The hyperlink likely directs to a fake login page harvesting credentials. |
| 4 | **Urgency / business context misuse** | Financial document reference to trick employees. | Uses social engineering—mixing finance terms and urgency. |
| 5 | **Brand impersonation** | Adobe logo, footer, and style mimic real Adobe emails. | Visual cloning increases trust; however, minor layout/font inconsistencies reveal forgery. |
| 6 | **Security warning** | Banner “You don’t often get email from …” & Microsoft ATP tag “Credential Phishing”. | Indicates automated detection of abnormal sender behavior. |

---

## 3. Header / technical clues (expected)
If headers were available, you’d verify:  
- `Return-Path` ≠ `@adobe.com`  
- SPF/DKIM/DMARC results: *fail*  
- `Received:` lines show non-Adobe servers  

---

## 4. Recommended response
- **Do not click** the “Open” button.  
- **Report** to IT Security / mark as phishing in Outlook.  
- **Block** sender domain and remove from mailbox.  
- **Educate** users to verify links before login.  

---

## 5. Tools used
- Microsoft ATP / Defender for Office 365  
- MXToolbox Header Analyzer (if full header available)  
- VirusTotal URL scan  

---

## 6. Conclusion
This email is a **credential-phishing attempt** using **brand impersonation** and **social engineering**.  
Indicators from both manual review and security-tool detection confirm it as **malicious**.
