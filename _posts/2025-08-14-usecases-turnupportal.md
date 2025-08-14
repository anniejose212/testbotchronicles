---
layout: default
title: "Use Cases for Time and Material Module – TurnUp Portal"
date: 2025-08-14
categories: [real-world-test-cases]
description: Detailed use cases for managing Time and Material entries in the TurnUp portal.
---

# Use Cases for Time and Material Module – TurnUp Portal

## Module Overview
The **Time and Material** module in TurnUp allows users to create, edit, and manage materials or time-based resources with details like type, code, description, price, and file attachments.

---

## **Use Case 1 – Add a New Material Entry**
**Actors:** Admin/User with permission  
**Precondition:** User is logged in with valid credentials.

**Steps:**
1. Navigate to `Administration > Time and Materials`.
2. Click **Create New**.
3. Select **TypeCode** as “Material”.
4. Enter a unique **Code** (e.g., `MAT101`).
5. Fill in **Description** (e.g., “Concrete Mix”).
6. Enter **Price per Unit**.
7. *(Optional)* Attach relevant files.
8. Click **Save**.

**Expected Result:**  
The new material appears in the list with correct details.

---

## **Use Case 2 – Edit an Existing Material**
**Precondition:** Material entry exists.

**Steps:**
1. Navigate to the material list.
2. Click **Edit** beside the target entry.
3. Update the description or price.
4. Save changes.

**Expected Result:**  
Material details are updated without affecting the code.

---

## **Use Case 3 – Delete a Material**
**Precondition:** Material exists and is not linked to active jobs.

**Steps:**
1. Go to the material list.
2. Click **Delete** beside the item.
3. Confirm deletion.

**Expected Result:**  
The material is removed from the list.

---

## **Use Case 4 – View Material List**
**Precondition:** User has view permissions.

**Steps:**
1. Navigate to the module.
2. Review all entries with their type, code, description, and price.

**Expected Result:**  
User can view a paginated list of materials.
