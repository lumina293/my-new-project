# User Story: Add Item Modal (LocalStorage)
**Epic:** Manual Product Inventory Input

## 1. Narrative
**As a** Staff Member,
**I want to** click an "Add Item" button to open a form,
**So that** I can record new stock arrival quickly without refreshing the page.

## 2. Acceptance Criteria
* [ ] **AC1 (The Interaction):**
    * Clicking "Add Item" opens a Modal (`Dialog`).
    * Form contains: Name (Text), Quantity (Number), Expiry (Date Picker).
* [ ] **AC2 (Validation - Zod Schema):**
    * `name`: String (5-200 chars). Error: "Name must be 5-200 characters."
    * `quantity`: Number (>0). Error: "Quantity must be positive."
    * `expiry`: Date (> Today). Error: "Expiry must be in the future."
* [ ] **AC3 (UX States):**
    * "Save" button is **Disabled** if form is invalid/dirty.
    * On Success: Modal closes, Toast appears ("Item Added"), List updates.
* [ ] **AC4 (Persistence):**
    * Data is saved to Browser `localStorage` key: `inventory-data`.

## 3. Technical Notes
* **State Management:** Use `useEffect` to read/write to LocalStorage to avoid Next.js Hydration Mismatch.
* **Components:**
    * `shadcn/ui/dialog`
    * `shadcn/ui/form` + `react-hook-form` + `zod`
    * `shadcn/ui/popover` + `shadcn/ui/calendar` (Date Picker)