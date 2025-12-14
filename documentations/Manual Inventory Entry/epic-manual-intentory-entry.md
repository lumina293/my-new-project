# Epic: Manual Inventory Entry
**Parent Initiative:** Near-Date Inventory Management System
**Status:** Ready for Development

## 1. Goal
To enable warehouse staff to populate the inventory system by manually entering product details. This is the foundational step to identifying near-date products.

## 2. Scope & Boundaries

### In Scope
* **Interface:** A web-based form accessible on Desktop and Mobile.
* **Workflow:** Single-item entry (one product at a time).
* **Automation:** The "Import Date" is automatically set to the current timestamp (Today).

### Out of Scope
* Batch import via CSV or Excel (Reserved for future Epics).
* Barcode scanning integration.

## 3. Functional Requirements

### Data Fields
| Field Name | Type | Required | Default Value | Notes |
| :--- | :--- | :--- | :--- | :--- |
| **Product Name** | Text | Yes | None | |
| **Quantity** | Number | Yes | None | Must be integer |
| **Expiry Date** | Date | Yes | None | Selected via Calendar UI |
| **Import Date** | Date | Yes | `Today` | Hidden from user |

### Validation Rules
1.  **Product Name:** Cannot be empty or whitespace only.
2.  **Quantity:** Must be greater than 0.
3.  **Expiry Date:** Must be strictly **after** Today (cannot enter already expired goods).

## 4. Success Criteria
* [ ] User fills out the form and clicks "Add Product".
* [ ] If valid, the form clears and the product appears immediately in the "Current Inventory" list.
* [ ] If invalid (e.g., past date), an error message appears below the specific field.

## 5. Technical Specifications (Draft Schema)

We will use **Zod** to enforce the validation rules defined above:

```typescript
const formSchema = z.object({
  name: z.string().min(1, { message: "Product name is required" }),
  quantity: z.coerce.number().min(1, { message: "Quantity must be at least 1" }),
  expiryDate: z.date().refine((date) => date > new Date(), {
    message: "Expiry date must be in the future",
  }),
});