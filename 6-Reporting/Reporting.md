<div align="center">

| Previous Phase | Main Page |
|:-------------------------------------------:|:-------------------------------------------:|
| [Post-Exploitation Page](5.0-Post-Exploitation.md) | [Landing Page](../README.md) | 

</div>

<br>
<br>

# Reporting

After having completed a penetration test. The artefacts from your tools are saved, and the shells are gone. But your most important deliverable remains: **the report**. This phase focuses on how to write professional, client-ready penetration testing reports that communicate what happened, why it matters, and what to do about it. You will not just learn how to explain vulnerabilities but also how to speak to both business and technical audiences.

We’ll break the process down into three core ideas:

* Why reporting matters - Reports are the only lasting output of your engagement. Teams change. Systems are updated. Reports stay.
* Who you’re writing for - Understand the different audiences (executives, developers, security engineers) and how to communicate with each.
* What makes a good report - Learn the structure, writing style, and remediation guidance to ensure your report is as useful as it can possibly be.

<br>

## The Structure of a Pentest Report

Every good report is built around a clear, logical format. This structure helps you present findings in a way that makes sense to both business and technical stakeholders. Before we can dive into the anatomy of a good report, we first need to understand the different audiences that your report should aim to address.

### Understanding the Audience

**Technical Stakeholders**
* **Goal:** Aid the technical team in understanding the root cause of the discovered vulnerabilities and what steps they will need to take to remediate them.
* **Who they are:** If you performed a pentest of a web application, this will most likely be the developers. If you assess a network, this will likely be the IT Support team.
* **Focus:** This is the most crucial audience.
* **Content Volume:** **70-90%** of your report is specifically aimed towards this audience.

**Security Stakeholders**
* **Goal:** Help prioritize remediation efforts and make sound judgement calls on which risks have to be addressed before the system goes live and which can be accepted.
* **Who they are:** Usually the organization's security function. They won't be directly responsible for remediating but will work closely with those that are.
* **Focus:** Prioritization and risk management.
* **Content Volume:** At least **10-20%** of the report should speak to this audience directly.

**Business Stakeholders**
* **Goal:** Help them understand the business impact of your findings (real-life impact if they choose not to remediate).
* **Who they are:** Individuals paying for the assessment. They are usually much less technical and more business-driven.
* **Motto:** *"Security must enable business, not fight against it."*
* **Content Volume:** At least **5-10%** of your report should speak to this audience in a manner abstracted from technical work.

<br>

### Sections of the Report

Now that we understand the audience our report needs to speak to, let's take a look at the three main sections that you would require:

| Section | Target Audience | Description |
| :--- | :--- | :--- |
| **Summary** | Business & Security Stakeholders | This is the high-level view of the assessment. It explains what was tested, what was found, and why it matters — all in business terms. It often includes an *Executive Summary* (strictly business terms) and a *Findings and Recommendation* section to aid security stakeholders in prioritization. |
| **Vulnerability Write-Ups** | Technical Stakeholders | This is the technical heart of the report. Each issue discovered during the test gets its own write-up, which will include details on the vulnerability, how it can be replicated, and the actions required for remediation. |
| **Appendices** | Security Stakeholders | Supporting details that don’t fit in the main report (e.g., detailed testing scope, methodology, or artefacts). These help security stakeholders better understand the coverage achieved and the next steps required post-remediation. |

<br>

### Why This Matters

A well-structured report makes it easier for your audience to take action. Business leaders can assess risk, and technical teams can start remediation. If your report lacks structure, even good findings might be ignored.


<br>
<br>
<br>

# Summary 

The summary plays a critical role in helping readers quickly understand the results of your assessment without needing to dive into the technical details. It connects your work to real-world business and security impact. The summary typically appears at the start of the report and should allow a reader, even someone without a technical background, to answer these questions:

* **What did we test?**
* **What did we find?**
* **What does it mean for our business or system?**
* **What should we do next?**

> **Note:** Ideally, you should write the summary **last**. If you haven't written the other sections, it will be hard to accurately summarise your findings.

<br>

### Summary of a Summary

In some cases, a single summary section is not enough to meet the needs of both business and security stakeholders. When this happens, it’s common to break the summary into two parts:

* **Executive Summary:** Written for **business stakeholders**, this version avoids technical jargon and focuses on business risk. It highlights the overall security posture and key concerns in a way that helps business stakeholders understand the impact of the findings and the actions that should be taken immediately.
* **Findings & Recommendations:** Written for the **security team**, this section details common vulnerability themes and attack chains. Vulnerabilities have risk ratings that are measured in isolation as if none of the other vulnerabilities existed. However, you may often find that the combination of two or more lower-risk vulnerabilities could still have high business impact. This is the section where you are able to highlight this to security stakeholders, helping them reprioritise remediation to address these issues. This section often draws links between issues and identifies systemic problems, allowing security stakeholders to use this information to help developers avoid future mistakes.

<br>

### Summary Structure

Regardless of whether you split the summary into two or keep it as one, a good summary should cover the following:

* **Overview:** What was tested? What type of system or application is it? What were the goals of the assessment? What was the scope, and how much coverage could be achieved?
* **Results:** What did the assessment uncover? Was the system secure? If not, what categories of issues were found?
* **Impact:** What is the real-world impact if the issues remain unaddressed? How could the system be exploited by a real-life threat actor?
* **Remediation Direction:** At a high level, what actions should the organisation take next? Does this require major investment, or are the issues mostly quick fixes?

The summary sets the tone for the entire report. If it’s too technical, business stakeholders will disengage. If it’s too vague, security teams won’t know what to do next. Knowing how and when to split the summary ensures your message reaches the right people, and leads to real action.


<br>
<br>

# Vulnerability Write-Ups

The largest section of your report will be the vulnerability write-ups. Each write-up should explain what the vulnerability is, where it was found, how it was discovered, and most importantly, how it should be remediated. 

This section is primarily written for the stakeholders who are going to fix the issues, such as developers or system administrators. However, others, such as security analysts and project managers, may also review these sections to track remediation, provide support, or validate severity.

### Structure of a Good Write-Up
To make your write-ups clear and actionable, you should follow a consistent structure for each one. Here's a format that works well:

* **Title:** A short, descriptive heading (e.g., "Unauthenticated SQL Injection in Login Form").
* **Risk Rating:** A risk rating for the discovered vulnerability. Vulnerabilities should always be rated in isolation, as if all other vulnerabilities did not exist. Use the client's risk rating matrix or a public one, such as CVSS.
* **Summary:** A brief explanation of the vulnerability and its potential impact in plain language.
* **Background:** Provide additional context to explain the vulnerability and why it matters. This is especially important if the reader is unfamiliar with it. Remember that the developers who will fix the vulnerability are potentially not security experts, so more guidance to help them understand the root cause will aid them in remediating the issue accurately.
* **Technical Details & Evidence:** Where and how the issue was found. Include requests, responses, payloads, and screenshots or code snippets if needed.
* **Impact:** What an attacker could realistically do with this vulnerability. Contextualize the impact to the specific system you are testing. For example, if tokens are used instead of cookies, does session hijacking still apply?
* **Remediation Advice:** Clear, actionable steps to resolve the issue. Your recommendation must address the **root cause** of the vulnerability, not just mitigate it. 
    * *Example:* For SQL Injection, while input validation helps, **parameterisation** is required to address the core issue. If you provide defense-in-depth controls (like WAF rules), mention that these cannot be implemented in isolation.
* **References:** (Optional) Links to relevant vendor documentation or guidance to support the fix.

<br>

### The Golden Thread
Although we are giving explicit sections here, reporting can eventually become so natural that you create the entire write-up without requiring these exact headings. A "golden thread" flows through your write-up, meaning readers can follow, understand, and know what to do next without requiring explicit headings. 

However, in cases where your report will be ingested by vulnerability management software, having discrete sections is often still beneficial. Ideally, you should tailor your report structure to the specific client's needs.

### Context Matters
Your report should never feel like it was copied from a textbook. The most valuable reports explain vulnerabilities in the context of the specific system tested. Your write-up should answer:

* **Where exactly was this found?** Be specific (endpoint, parameter, or feature).
* **What assumptions are required?** Does the attacker need credentials? Is it only exploitable during a certain workflow?
* **How does this affect this client’s environment?** Could it leak patient data (hospital)? Could it affect transactions (e-commerce)?
* **What steps should this client take?** Go beyond generic fixes. If they use C# with MS SQL, show a specific example for that stack.

<br>

### Example: SQL Injection Write-Up

**Title:** Unauthenticated SQL Injection in Login Form  
**Risk Rating:** High (CVSS 3.1 Base Score: 8.6)  

**Summary:** An unauthenticated SQL injection vulnerability was identified in the login form of the TryBankMe application. This could allow an attacker to bypass authentication or extract sensitive customer information.

**Background:** SQL Injection occurs when user-supplied input is unsafely included in SQL queries without proper parameterisation. The SQL interpreter is unable to discern SQL commands from the user-supplied input, leading to confusion that allows a threat actor to inject directly into the SQL command itself.

**Technical Details & Evidence:** The login form at `/login` was vulnerable to SQL Injection via the `username` field. Using Burp Suite, the following HTTP request was intercepted and modified:

```http
POST /login HTTP/1.1
Host: trybankme.com
Content-Type: application/x-www-form-urlencoded
Content-Length: 45

username=' OR 1=1--&password=randomvalue
```

The application responded with a 302 Found redirect to the authenticated user dashboard:

```http
HTTP/1.1 302 Found
Location: /dashboard
Set-Cookie: sessionid=abc123xyz456; Path=/; HttpOnly
```

This confirmed that authentication was bypassed using a classic SQL Injection payload.

**Impact:**
An attacker could log in as any user without valid credentials. Furthermore, even though the injection points were blind, a threat actor could leverage error-based injections to enumerate information from the database.

**Remediation Advice:**
Parameterised queries should be used for all database operations involving user input. For example, in a .NET application using MS SQL, the login query should be altered to look like this:

```csharp
using (SqlConnection connection = new SqlConnection(connectionString))
{
    string query = "SELECT * FROM Users WHERE Username = @username AND Password = @password";
    SqlCommand command = new SqlCommand(query, connection);
    
    // Add parameters safely
    command.Parameters.AddWithValue("@username", inputUsername);
    command.Parameters.AddWithValue("@password", inputPassword);
    
    connection.Open();
    SqlDataReader reader = command.ExecuteReader();
    
    if (reader.HasRows)
    {
        // Login successful
    }
}
```

> As shown in the example above, the user input is distinctly split from the SQL command, ensuring that the SQL engine cannot be confused.

<br>
<br>

# Appendices

Appendices are especially useful for security stakeholders and future testers who may need to validate what was done, verify the scope, or follow up after remediation. There isn't usually a fixed format for appendices, and the format may vary from project to project. However, there are two main appendices that you should always aim to include in your report.

### Assessment Scope
The assessment scope appendix should be used to establish how close the assessment was to what was originally scoped in the Rules of Engagement document. It may be that changes were made during the project or that it was impossible to gain coverage of the entire scope for various reasons. 

The assessment scope appendix is the perfect place to provide this information which can help security stakeholders understand the next steps. For example, if you were only able to gain coverage of 80% of the scope, a complete reassessment for the remaining 20% will probably be required, depending on how many vulnerabilities were discovered during the initial test.

### Assessment Artefacts
The assessment artefacts appendix provides you with an opportunity to list out any changes that you may have made during your testing. While you should always aim to perform your own cleanup, it is often impossible to fully remove all artefacts created due to security testing. This is crucial information as some of these artefacts may be potentially malicious.

For example, you may have uploaded a webshell by leveraging an unrestricted file upload vulnerability. In the worst possible case, two years later everyone forgets about the file and the pentest, only to rediscover it and raise it as an actual security incident! This appendix allows you to provide these artefacts and recommendations on which of these artefacts need to be removed and how they should be removed.

You should think of the appendices as your audit trail. It shows your work, backs up your findings, and allows for informed follow-up, long after the initial assessment is over.

<br>
<br>

# Writing the Report

Writing a report isn’t just about getting information on the page; it is about communicating that information clearly, objectively, and professionally. It is the only part of your pentest that will stand the test of time. Long after you have moved on to a different career or the entire project team has changed, the report will still be relevant.

### Writing Clearly
Clarity is one of the most important qualities of a good report. You should always aim to avoid ambiguity by using simple and direct language that makes your point obvious. Your writing should be understandable even to readers who do not have deep knowledge of the system. If your meaning is unclear or buried under unnecessary complexity, your findings are less likely to be taken seriously, or even fixed.

### Professional Writing
A pentest report is a formal document. Use the same tone and style that you would in any other business-critical communication. This means:

* **Be objective** - Stick to the facts. Avoid exaggeration, emotional language, or assumptions about intent.
* **Avoid informal writing** - No slang, no jokes, and no "we pwned the login page."
* **Be consistent** - Use the same terminology, formatting, and structure throughout the report. Avoid switching between different spellings or terms for the same thing.

### General Best Practices
Follow these simple rules to improve the professionalism and readability of your writing:

* **Write in past tense** - E.g. "The vulnerability was discovered during authentication testing."
* **Do not use first-person language** - Avoid "I," "we," "our," and "us." Write as a neutral observer.
* **Mask sensitive information** - Never include real passwords or other private data unless explicitly authorised. If you have a screenshot to show impact of a vulnerability, make sure to blur any sensitive information.
* **Use clean, formal phrasing** - Avoid contractions and overly casual terms. "The attacker gained unauthorised access" is better than "we broke in."

### Quality Assurance (QA) Process
Even experienced testers can make mistakes. This is why every report should go through a proper review process:

* **Read your own work** - Step away from the report and come back to it later with fresh eyes. Look for unclear sentences, inconsistencies, or missing context. It can usually help to read your writing out loud for yourself.
* **Get someone else to read your work** - A peer reviewer should check that your findings are understandable, actionable, and professionally written.

QA isn’t just about fixing typos. It’s about making sure the report reflects well on both you and your pentesting team.

You can have the best technical findings in the world, but if your report is sloppy, emotional, inconsistent, or unclear, it will not have the impact it should. Good writing helps good security work get the attention it deserves.

<br>

> **External References:**
> * [**Public Pentesting Reports (GitHub)**](https://github.com/juliocesarfort/public-pentesting-reports) - A massive curated list of public penetration test reports released by various firms (Cure53, NCC Group, Offensive Security). **Highly Recommended.**
> * [**Offensive Security Sample Report**](https://www.offensive-security.com/pwk-online/PWK-Example-Report-v1.pdf) - The official sample report for the OSCP certification. It sets the standard for what a "Junior Pentester" report should look like.
> * [**CVSS v3.1 Calculator**](https://www.first.org/cvss/calculator/3.1) - The industry standard calculator for scoring vulnerabilities based on Exploitability and Impact.
> * [**OWASP Risk Rating Methodology**](https://owasp.org/www-community/OWASP_Risk_Rating_Methodology) - A methodology specifically tailored for web applications, focusing on "Likelihood" vs. "Impact."
> * [**DREAD Rating System**](https://en.wikipedia.org/wiki/DREAD_(risk_assessment_model)) - An older but simpler classification scheme (Damage, Reproducibility, Exploitability, Affected Users, Discovery) often used by Microsoft.
> * [**PTES Reporting Standard**](http://www.pentest-standard.org/index.php/Reporting) - The "Penetration Testing Execution Standard" section dedicated entirely to what a report must contain.
> * [**OSSTMM 3**](https://www.isecom.org/OSSTMM.3.pdf) - The Open Source Security Testing Methodology Manual. It provides a scientific approach to measuring security and reporting on "operational security."
> * [**Dradis Framework**](https://dradisframework.com/ce/) - An open-source collaboration and reporting platform. It imports output from tools (Nmap, Burp, Nessus) and helps generate the final Word/PDF report.
> * [**DefectDojo**](https://github.com/DefectDojo/django-DefectDojo) - An open-source vulnerability management tool that streamlines the testing process and report generation.
> * [**Serpico**](https://github.com/SerpicoProject/Serpico) - "SimplE RePort wrIting and COllaboration." A tool specifically built to speed up report writing by using templates.


<br>

---

<br>
<br>

<div align="center">

| Previous Phase | Main Page |
|:-------------------------------------------:|:-------------------------------------------:|
| [Post-Exploitation Page](5.0-Post-Exploitation.md) | [Landing Page](../README.md) | 

</div>