---
layout: default
title: "Time & Material — Test Scenarios and Test Cases"
date: 2025-08-14
categories: [real-world-test-cases]
description: End-to-end test scenarios and executable test cases for the Time & Material module in TurnUp.
---
# Time & Material — Test Scenarios and Test Cases

## 1) Scope & Notes
- **Screen:** Administration ▸ Time and Materials (Create/Edit/List)
- **Fields:** TypeCode (dropdown), Code (text), Description (text), Price per unit (numeric), Attachments (file), Save, Back to List.
- **Assumptions (confirm with BA/Dev):**
  - Unique **Code** (system-wide).
  - **Price per unit** accepts positive decimals; 2 d.p. rounding on save.
  - Max lengths: Code=20, Description=200 (TBD).
  - Allowed TypeCodes: *Material*, *Time* (TBD).
  - Attachments: PDF/JPG/PNG ≤ 5MB each (TBD).
  - AuthZ: Only Admin can Create/Edit/Delete; Viewer can List.

---

## 2) High-Level Test Scenarios
1. **Create** new Time/Material item (happy path).
2. **Edit** existing item (change Description/Price).
3. **Delete** item (with/without dependencies).
4. **List/View** items (paging, sorting, basic search/filter if available).
5. **Validation**: required fields, formats, lengths, uniqueness.
6. **TypeCode behavior**: defaults, switching Time vs Material.
7. **Price behavior**: decimals, currency formatting, rounding.
8. **Attachments**: upload valid file, invalid type/size, multiple files.
9. **Navigation/UX**: Save, Cancel/Back to List, unsaved changes warning.
10. **Security**: role-based access (Admin vs Viewer), direct-URL access.
11. **Concurrency**: simultaneous edit; deleted item not editable.
12. **Performance**: save/list response under N seconds (TBD).
13. **Audit/Metadata**: created/updated by, timestamps (if present).
14. **Localization**: decimal separators (., ,) if locale applies.
15. **Reliability**: server/network error handling, graceful messages.

---

## 3) Test Data (sample)
- Codes: `MAT001`, `TIM001`, `DUP001`
- Descriptions: "Concrete mix M20", "On-site labor hour"
- Prices: `0`, `1`, `9.99`, `1000.5`, `123456.78`, `-1`(neg), `abc` (invalid)
- Files: 
  - Valid: `quote.pdf` (300KB), `image.png` (200KB) 
  - Invalid type: `script.exe`
  - Oversize: `large.pdf` (6MB)

---

## 4) Test Cases

### Create
| ID | Title | Precondition | Steps | Expected |
|---|---|---|---|---|
| TM-CR-01 | Create **Material** (happy path) | Logged in as Admin | Admin ▸ Time & Materials ▸ Create; TypeCode=Material; Code=`MAT001`; Description="Concrete mix M20"; Price=`9.99`; Save | Success toast; record listed with exact values; price shown `9.99` |
| TM-CR-02 | Create **Time** (hourly) | Admin | Create; TypeCode=Time; Code=`TIM001`; Description="On-site labor"; Price=`100`; Save | Record saved as Type=Time |
| TM-CR-03 | **Required fields** | Admin | Leave Code blank; fill others; Save | Inline error for Code; save blocked |
| TM-CR-04 | **Unique Code** validation | `DUP001` already exists | Create with Code=`DUP001`; Save | Error "Code must be unique"; save blocked |
| TM-CR-05 | **Code length** boundary | Admin | Enter Code with 20 chars; Save | Accepts; saved |
| TM-CR-06 | **Code too long** | Admin | Enter Code with 21+ chars; Save | Validation message; blocked |
| TM-CR-07 | **Price decimal** support | Admin | Price=`123456.78`; Save | Saved; price rounded/displayed to 2 d.p. |
| TM-CR-08 | **Price = 0** | Admin | Price=`0`; Save | Accept (if allowed) OR validation (confirm rule) |
| TM-CR-09 | **Negative price** | Admin | Price=`-1`; Save | Validation error; blocked |
| TM-CR-10 | **Non-numeric price** | Admin | Price=`abc`; Save | Validation error |
| TM-CR-11 | **Attach valid file** | Admin | Add `quote.pdf`; Save | Saved; file listed/linked |
| TM-CR-12 | **Invalid file type** | Admin | Add `script.exe`; Save | Error "File type not allowed" |
| TM-CR-13 | **Oversized file** | Admin | Add `large.pdf` (6MB); Save | Error "File exceeds limit" |
| TM-CR-14 | **Multiple attachments** | Admin | Add `quote.pdf` + `image.png`; Save | Both retained after save |
| TM-CR-15 | **Cancel / Back to List** | Admin | Enter some data; click Back to List/Cancel | Prompt to discard; no record created when confirmed |

### Edit
| ID | Title | Precondition | Steps | Expected |
|---|---|---|---|---|
| TM-ED-01 | Edit Description | Item `MAT001` exists | Open Edit; change Description; Save | Updated on list/detail |
| TM-ED-02 | Edit Price rounding | Item exists | Set Price=`1000.5`; Save | Stored/Shown as `1000.50` |
| TM-ED-03 | Change Code to **duplicate** | `DUP001` exists | Edit other item; set Code=`DUP001`; Save | Unique constraint error |
| TM-ED-04 | Switch TypeCode | Item exists | Change Material→Time (if allowed); Save | Either saved (if business rule allows) *or* blocked with clear message |
| TM-ED-05 | Unsaved changes warning | Item exists | Modify fields; try Back to List | Prompt appears; staying keeps changes; leaving discards |

### Delete
| ID | Title | Precondition | Steps | Expected |
|---|---|---|---|---|
| TM-DE-01 | Delete item (no dependencies) | Item exists | Click Delete ▸ Confirm | Removed from list |
| TM-DE-02 | Delete item **with dependency** | Item linked to Jobs (mock/seed) | Delete ▸ Confirm | Blocked with explanatory error |
| TM-DE-03 | Delete **cancel** flow | Item exists | Delete ▸ Cancel | Item remains |

### List / View / Search
| ID | Title | Precondition | Steps | Expected |
|---|---|---|---|---|
| TM-LI-01 | List loads | N/A | Open module | Table shows columns Type, Code, Description, Price |
| TM-LI-02 | Sort by Code | Multiple items | Click Code header | Sort asc/desc toggles; stable |
| TM-LI-03 | Filter/Search by Code | Search available | Enter `MAT` | Only matching records shown |
| TM-LI-04 | Pagination | >1 page data | Navigate pages | Correct counts; no duplicates |
| TM-LI-05 | Column **currency format** | Items with decimals | View list | Price shows 2 d.p.; thousand separators if configured |

### Security / Roles
| ID | Title | Precondition | Steps | Expected |
|---|---|---|---|---|
| TM-SE-01 | Viewer cannot **Create** | Logged in as Viewer | Access Create URL/button | Access denied or button hidden |
| TM-SE-02 | Viewer cannot **Edit/Delete** | Viewer | Click Edit/Delete | Denied with friendly message |
| TM-SE-03 | Direct URL protection | Viewer | Paste `/TimeAndMaterials/Edit/{id}` | 403/redirect to login/denied |

### Concurrency / Reliability
| ID | Title | Precondition | Steps | Expected |
|---|---|---|---|---|
| TM-CC-01 | Simultaneous edit | Two Admins | A opens Edit; B changes Price and saves; A saves | A gets conflict warning or last-write policy documented |
| TM-CC-02 | Delete while editing | Item open in Edit | From another session delete the item; return and save in A | A gets "record not found" and redirected safely |
| TM-CC-03 | Network/server error on save | Simulate 500/timeout | Save | User sees retryable, meaningful error; no duplicate created |

### Non-functional (quick checks)
| ID | Title | Expected |
|---|---|---|
| TM-NF-01 | Save completes under **2s** with normal load | ≤ 2s (TBD SLA) |
| TM-NF-02 | Upload ≤5MB file under **3s** | ≤ 3s on test network |
| TM-NF-03 | Basic accessibility | Labels tied to inputs; keyboard nav; color contrast |

---

## 5) Traceability (Scenarios → Cases)
- **Create:** TM-CR-01..15  
- **Edit:** TM-ED-01..05  
- **Delete:** TM-DE-01..03  
- **List/View/Search:** TM-LI-01..05  
- **Security:** TM-SE-01..03  
- **Concurrency/Reliability:** TM-CC-01..03  
- **Non-functional:** TM-NF-01..03

---

- Factor common steps (login, navigate to module) into helper methods.

