# Initiative: Near-Date Inventory Management System

## 1. Executive Summary
**Vision:** A specialized dashboard to help supermarket managers identify products approaching their expiry date. This tool enables timely clearance promotion campaigns to reduce waste and maximize revenue on expiring stock.
**Target Audience:** Supermarket Managers and Inventory Staff.

## 2. Success Metrics (KPIs)
* **Visibility:** 100% of products expiring within the next 60 days are flagged and visible to staff.
* **User Value:** Drastic reduction in wasted inventory (expired goods) through early detection.

## 3. High-Level Scope

### Core Inputs (Data Entry)
The system accepts manual entry or mock-data loading of stock items containing:
* **Product Name** (String)
* **Quantity** (Number)
* **Expiry Date** (Date)

### Core Outputs (Dashboard)
A filtered view focusing strictly on "At Risk" items:
1.  **Critical List:** Products expiring within **30 days**.
2.  **Warning List:** Products expiring between **31-60 days**.
3.  **Safe List:** (Optional/Hidden) Products expiring > 60 days.

### Logic & Rules
* **The "60-Day" Rule:** Any product with `ExpiryDate <= Today + 60 Days` is considered "Near-Date".
* **Sorting:** Default sort order is by `ExpiryDate` (Ascending) -> Nearest expiry first.

## 4. Technical Constraints & Architecture

### Tech Stack
* **Framework:** Next.js 14+ (App Router)
* **Language:** TypeScript
* **Styling:** Tailwind CSS
* **UI Library:** Shadcn UI (Radix Primitives)
* **State Management:** React Hook Form + Zod (Validation)

### Design System
* **Theme:** Professional / Clean.
* **Palette:** Shadcn `Slate` (Gray/Neutral) with semantic colors for status (Red for Critical, Yellow for Warning).
* **Responsiveness:** **Desktop-First** (Optimized for back-office management tables), but functional on mobile.

## 5. Data Model (Draft)
```typescript
export interface Product {
  id: string; // UUID
  name: string;
  quantity: number;
  expiryDate: Date;
  status: 'CRITICAL' | 'WARNING' | 'SAFE'; // Derived from logic
}