# Initiative: Supermarket "Near-Date" Inventory Clearance

## 1. Executive Summary
**Vision:** An operational dashboard enabling supermarket staff to proactively identify near-expiry products and instantly flag them for clearance campaigns, reducing waste and revenue loss.

**Target Audience:** Supermarket Floor Staff & Managers.

## 2. Success Metrics (KPIs)
* **Visibility:** 100% of products expiring within 60 days are auto-surfaced to staff.
* **Efficiency:** Staff can transition an item to "Clearance Mode" in 1 click.
* **Safety:** Expired items are strictly segregated from sellable inventory to prevent accidental sales.

## 3. High-Level Scope
* **Core Inputs:** Manual entry form (Name, Quantity, Expiry Date).
* **Logic Buckets:**
    1.  **Expired:** `Expiry Date < Today` (Move to "Expired" Table).
    2.  **Near-Date:** `Today <= Expiry Date <= (Today + 60 Days)` (Show in "Action List").
    3.  **Safe:** `Expiry Date > (Today + 60 Days)` (Hidden from urgent view).
* **Actions:**
    * "Promote" button changes status to `ON_CLEARANCE`.
    * List defaults to **ASC** sorting (Earliest expiry first).

## 4. Technical Constraints & Style
* **Stack:** Next.js (App Router), TypeScript, Tailwind, Shadcn UI.
* **Theme:** Shadcn 'Slate' (Clean, data-heavy professional look).
* **Device:** Desktop-First (Optimized for back-office usage).