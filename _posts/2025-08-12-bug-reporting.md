---
layout: default
title: "Bug Reporting Essentials"
date: 2025-08-12
categories: [manual-mastery]
description: A step-by-step guide to logging defects effectively, ensuring clarity and faster resolution.
---

Accurate bug logging is essential for effective defect management. A well-documented bug helps developers reproduce, investigate, and fix issues quickly.

---

## 📌 Steps to Log a Bug

1. **Access the Defect Tracking Tool**  
   - Open your tool of choice (e.g., Jira, Azure DevOps, Bugzilla).  

2. **Create a New Issue**  
   - Click **"Create"** or equivalent to start logging the bug.  

3. **Write a Clear Title**  
   - Summarise the problem in one line.  
   - *Example:* “Login button unresponsive on Chrome v110.”  

4. **Provide Detailed Steps to Reproduce**  
   - List each step in order to replicate the defect.  

5. **Specify Expected vs. Actual Results**  
   - *Expected:* Login form should submit and redirect to dashboard.  
   - *Actual:* Button click does nothing.  

6. **Attach Supporting Evidence**  
   - Screenshots, videos, or logs that illustrate the issue.  

7. **Set Severity and Priority**  
   - Severity reflects impact; priority determines fix urgency.  

8. **Assign to the Relevant Team Member**  
   - Route the bug to the correct developer or team.

---

## 💡 Example Bug Report

**Title:** Login button unresponsive on Chrome v110  
**Environment:** Windows 11, Chrome v110  
**Steps to Reproduce:**  
1. Open the login page.  
2. Enter valid username and password.  
3. Click the login button.  

**Expected Result:** User is redirected to dashboard.  
**Actual Result:** Button click has no effect.  

**Severity:** High  
**Priority:** P1  
**Attachments:** Screenshot and console log file.

---

## ✅ Best Practices
- Keep bug titles concise but descriptive  
- Provide complete reproduction steps  
- Always include environment details  
- Attach evidence to speed up debugging  
- Avoid vague statements like “It’s not working”
