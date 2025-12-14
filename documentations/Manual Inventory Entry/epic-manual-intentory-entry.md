# Epic: Manual Product Inventory Input
**Parent Initiative:** Supermarket "Near-Date" Inventory Clearance

## 1. Goal
Enable staff to manually log new inventory items into the system via a validated modal form, ensuring only clean, sellable data enters the database.

## 2. Scope & Boundaries
* **In Scope:**
    * **Trigger:** "Add Item" button opening a Modal.
    * **Form:** Inputs for Name, Quantity, Expiry Date.
    * **Validation (Zod Schema):**
        * `productName`: String (5 - 200 chars).
        * `quantity`: Integer (Min: 1).
        * `expiryDate`: Date (Must be >= Today).
    * **Hidden Fields:** `createdAt` (Server-side timestamp).
* **Out of Scope:** Bulk upload (CSV/Excel).

## 3. UI/UX Concept
* **Interaction:** * Main "Add Items" button (Top Right).
    * Modal overlay with focus trap.
    * "Save" button is **Disabled** by default, becomes **Primary** only when form is valid.
* **Feedback:** Real-time inline error messages (e.g., "Name is too short") below the input fields.