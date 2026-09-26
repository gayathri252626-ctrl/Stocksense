# 📦 StockSense — Complete Git Commits Reference (Steps 1 – 4)

This repository (`stocksense`) has been initialized with a clean, professional, conventional Git history consisting of **15 atomic commits** structured chronologically across **Step 1, Step 2, Step 3, and Step 4**.

---

## 🚀 How to Push All Commits to GitHub (1-Minute Guide)

Since this directory **already contains the initialized `.git` repository with all 15 commits**, you do not need to create commits manually. Just link it to your GitHub repository and push:

1. Create a new repository on **[github.com/new](https://github.com/new)** (e.g. named `stocksense`). Leave *"Add README"* and *".gitignore"* **unchecked**.
2. Open PowerShell or Command Prompt in this folder:
   ```powershell
   cd "C:\Users\Gokulram M\Downloads\stocksense"
   ```
3. Set default branch to `main`, add your remote origin, and push:
   ```bash
   git branch -M main
   git remote add origin https://github.com/<YOUR-GITHUB-USERNAME>/stocksense.git
   git push -u origin main
   ```
*All 15 commits across all 4 steps will immediately appear in chronological order on your GitHub repository!*

---

## 📜 Full Breakdown of All 15 Commits

### 🔹 STEP 1: Foundation, Data Models & Authentication

#### Commit 1: Project Scaffolding & Monorepo Setup
- **SHA**: `30f139e`
- **Message**:
  ```text
  chore: initialize project scaffolding and workspace configuration

  - Add root package.json and workspace scripts
  - Configure .gitignore for Node, Vite, and environment files
  - Establish monorepo structure for server and client
  ```
- **Files**:
  - `.gitignore`
  - `package.json`

#### Commit 2: Express Server, MongoDB Connection & All 11 Mongoose Schemas
- **SHA**: `3124f01`
- **Message**:
  ```text
  feat(server): setup Express server, MongoDB connection, and Mongoose schemas

  - Configure MongoDB connection with automatic in-memory fallback
  - Define 11 core Mongoose schemas: User, OtpToken, Warehouse, Category, Product, StockLevel, StockLedger, Receipt, DeliveryOrder, InternalTransfer, Adjustment
  - Create database seed script with manager and staff demo accounts
  ```
- **Files**:
  - `server/package.json`
  - `server/.env.example`
  - `server/src/config/db.js`
  - `server/src/models/User.js`
  - `server/src/models/OtpToken.js`
  - `server/src/models/Warehouse.js`
  - `server/src/models/Category.js`
  - `server/src/models/Product.js`
  - `server/src/models/StockLevel.js`
  - `server/src/models/StockLedger.js`
  - `server/src/models/Receipt.js`
  - `server/src/models/DeliveryOrder.js`
  - `server/src/models/InternalTransfer.js`
  - `server/src/models/Adjustment.js`
  - `server/src/models/index.js`
  - `server/src/seed.js`

#### Commit 3: Authentication API, Role Guards & OTP Password Reset
- **SHA**: `ea0b3ba`
- **Message**:
  ```text
  feat(auth): implement JWT authentication, role guards, and OTP password recovery

  - Implement signup, login, and token verification with bcrypt & JWT
  - Build 6-digit OTP password reset workflow with 10-minute expiry
  - Add role-based access control middleware (manager vs staff)
  - Setup Socket.io real-time server and auth verification test script
  ```
- **Files**:
  - `server/src/controllers/authController.js`
  - `server/src/routes/authRoutes.js`
  - `server/src/middleware/auth.js`
  - `server/src/middleware/errorHandler.js`
  - `server/src/socket.js`
  - `server/src/server.js`
  - `server/src/testAuth.js`

#### Commit 4: Client Tooling, TailwindCSS Theme & Navigation Layout
- **SHA**: `f87e301`
- **Message**:
  ```text
  feat(client): configure Vite, TailwindCSS design system, and core app layout

  - Configure Vite 5 build tool, TailwindCSS, PostCSS, and Autoprefixer
  - Build dark/light theme foundation, typography, and glassmorphic styles
  - Create responsive Layout with collapsible Sidebar and modern Navbar
  - Configure Axios HTTP interceptor and Auth/Socket React contexts
  ```
- **Files**:
  - `client/package.json`
  - `client/vite.config.js`
  - `client/tailwind.config.js`
  - `client/postcss.config.js`
  - `client/index.html`
  - `client/.env.example`
  - `client/src/index.css`
  - `client/src/api/axios.js`
  - `client/src/context/AuthContext.jsx`
  - `client/src/context/SocketContext.jsx`
  - `client/src/components/layout/Navbar.jsx`
  - `client/src/components/layout/Sidebar.jsx`
  - `client/src/components/layout/Layout.jsx`

#### Commit 5: Client Authentication Pages & Protected Routing
- **SHA**: `54b2d96`
- **Message**:
  ```text
  feat(client): implement authentication pages, OTP recovery flow, and protected routing

  - Build Login page with demo credentials quick-fill buttons
  - Build Signup page with role selection (Manager / Staff)
  - Build Forgot Password & Reset Password OTP verification pages
  - Implement protected route guards and core navigation pages
  - Wire React Router v6 in App.jsx and mount in main.jsx
  ```
- **Files**:
  - `client/src/pages/auth/Login.jsx`
  - `client/src/pages/auth/Signup.jsx`
  - `client/src/pages/auth/ForgotPassword.jsx`
  - `client/src/pages/auth/ResetPassword.jsx`
  - `client/src/pages/profile/ProfilePage.jsx`
  - `client/src/App.jsx`
  - `client/src/main.jsx`

---

### 🔹 STEP 2: Products, Warehouses & Dashboard KPIs

#### Commit 6: Master Product Catalog & Reorder Points
- **SHA**: `3f0b589`
- **Message**:
  ```text
  feat(products): build master product catalog with SKU search and location breakdown

  - Create product management CRUD endpoints with warehouse stock breakdown
  - Build ProductsPage UI with live search, category filtering, and stock modal
  - Implement reorder point indicators and low-stock badges
  ```
- **Files**:
  - `server/src/routes/productRoutes.js`
  - `client/src/pages/products/ProductsPage.jsx`

#### Commit 7: Facility & Category Settings
- **SHA**: `dda7aa0`
- **Message**:
  ```text
  feat(settings): implement warehouse and category management CRUD

  - Add warehouse and category management API endpoints with stock counters
  - Implement WarehouseSettingsPage with tabs for facilities and categories
  - Enable creation, editing, and code management for multi-warehouse tracking
  ```
- **Files**:
  - `server/src/routes/warehouseRoutes.js`
  - `server/src/routes/categoryRoutes.js`
  - `client/src/pages/settings/WarehouseSettingsPage.jsx`

#### Commit 8: Real-Time Dashboard KPIs & Low-Stock Alerts
- **SHA**: `f4a5a3e`
- **Message**:
  ```text
  feat(dashboard): build real-time KPIs, dynamic multi-filters, and low-stock alert banner

  - Build dashboard controller aggregating 5 core KPIs and document filters
  - Create Dashboard UI with dynamic filter bar (type, status, warehouse, category)
  - Add reactive low-stock alert banner with direct restock actions
  - Wire live updates via SocketContext
  ```
- **Files**:
  - `server/src/controllers/dashboardController.js`
  - `server/src/routes/dashboardRoutes.js`
  - `client/src/pages/dashboard/Dashboard.jsx`

---

### 🔹 STEP 3: Receipts (Incoming), Deliveries (Outgoing) & Engine

#### Commit 9: Inbound Receipts Module & Atomic Validation
- **SHA**: `4c7d5b0`
- **Message**:
  ```text
  feat(receipts): implement incoming stock receipts with atomic validation

  - Add Receipt API with supplier, warehouse, and multi-line item tracking
  - Build atomic validation: increments StockLevel, writes StockLedger record, marks done
  - Implement ReceiptsPage UI with status filters, search, modal, and drawer
  - Broadcast Socket.io stock:update events on validation
  ```
- **Files**:
  - `server/src/routes/receiptRoutes.js`
  - `client/src/pages/receipts/ReceiptsPage.jsx`

#### Commit 10: Outbound Delivery Orders & Negative Stock Prevention
- **SHA**: `93fa4cc`
- **Message**:
  ```text
  feat(deliveries): implement outgoing delivery orders with negative stock prevention

  - Add DeliveryOrder API with picking and packing status lifecycle
  - Pre-check stock sufficiency and strictly reject negative stock with HTTP 400
  - Decrement StockLevel, write negative StockLedger record, and emit socket updates
  - Implement DeliveryOrdersPage UI with per-line stock sufficiency indicator badges
  ```
- **Files**:
  - `server/src/routes/deliveryRoutes.js`
  - `client/src/pages/deliveries/DeliveryOrdersPage.jsx`

#### Commit 11: Step 3 Verification Test Suite
- **SHA**: `36407b5`
- **Message**:
  ```text
  test(step3): add automated test suite for receipt validation and negative stock prevention

  - Create testStep3.js to execute complete verification loop
  - Test receipt validation (+50), excessive delivery rejection (400), and valid dispatch (-20)
  - Confirm live Socket.io broadcast delivery
  ```
- **Files**:
  - `server/src/testStep3.js`

---

### 🔹 STEP 4: Internal Transfers, Adjustments & Move History Ledger

#### Commit 12: Internal Transfers (Inter-Facility Relocation)
- **SHA**: `8fcb6f4`
- **Message**:
  ```text
  feat(transfers): implement multi-location internal transfers with atomic balance relocation

  - Add InternalTransfer API with origin stock validation and negative stock block
  - Shift StockLevel atomically from origin to destination warehouse in one operation
  - Log simultaneous transfer_out and transfer_in audit records to StockLedger
  - Build TransfersPage UI with route visual cards, live stock hints, and validation action
  ```
- **Files**:
  - `server/src/routes/transferRoutes.js`
  - `client/src/pages/transfers/TransfersPage.jsx`

#### Commit 13: Stock Adjustments (Physical Count Reconciliation)
- **SHA**: `0739303`
- **Message**:
  ```text
  feat(adjustments): implement physical count inventory reconciliation with automatic ledger sync

  - Add Stock Adjustments API fetching live recorded stock and applying verified counts
  - Synchronize StockLevel to physical count and log discrepancy delta to StockLedger
  - Build AdjustmentsPage UI with live system stock preview, real-time diff badge, and reasons
  ```
- **Files**:
  - `server/src/routes/adjustmentRoutes.js`
  - `client/src/pages/adjustments/AdjustmentsPage.jsx`

#### Commit 14: Move History & StockLedger Audit Trail
- **SHA**: `0a697e1`
- **Message**:
  ```text
  feat(ledger): implement Move History audit trail with smart filters and CSV export

  - Build StockLedger query API with multi-dimensional filters (product, warehouse, type, date range)
  - Calculate audit metrics: total inflow, total outflow, and net inventory delta
  - Build MoveHistoryPage UI with movement type badges, Socket.io auto-refresh, and CSV export
  ```
- **Files**:
  - `server/src/routes/ledgerRoutes.js`
  - `client/src/pages/move-history/MoveHistoryPage.jsx`

#### Commit 15: Operational Lifecycle Test & Real-Time Documentation
- **SHA**: `a37d243`
- **Message**:
  ```text
  docs: full operational lifecycle test and comprehensive real-time architecture guide

  - Add testStep4.js verifying complete 4-stage operational loop: receipt, transfer, delivery, adjustment
  - Update README with in-depth Socket.io event architecture and payload contracts
  - Add commit guides and verify zero-defect end-to-end operation
  ```
- **Files**:
  - `server/src/testStep4.js`
  - `README.md`
  - `GIT-COMMITS-STEP1.md`
  - `GIT-COMMITS-STEP4.md`

---

## 🛠️ Manual Step-by-Step Git Commands (Alternative)

If you ever wish to execute all commits manually in a clean directory from scratch:

```bash
# 1. Initialize
git init -b main

# STEP 1
git add .gitignore package.json
git commit -m "chore: initialize project scaffolding and workspace configuration"

git add server/package.json server/.env.example server/src/config/db.js server/src/models/ server/src/seed.js
git commit -m "feat(server): setup Express server, MongoDB connection, and Mongoose schemas"

git add server/src/controllers/authController.js server/src/routes/authRoutes.js server/src/middleware/ server/src/socket.js server/src/server.js server/src/testAuth.js
git commit -m "feat(auth): implement JWT authentication, role guards, and OTP password recovery"

git add client/package.json client/vite.config.js client/tailwind.config.js client/postcss.config.js client/index.html client/.env.example client/src/index.css client/src/api/ client/src/context/ client/src/components/
git commit -m "feat(client): configure Vite, TailwindCSS design system, and core app layout"

git add client/src/pages/auth/ client/src/pages/profile/ client/src/App.jsx client/src/main.jsx
git commit -m "feat(client): implement authentication pages, OTP recovery flow, and protected routing"

# STEP 2
git add server/src/routes/productRoutes.js client/src/pages/products/ProductsPage.jsx
git commit -m "feat(products): build master product catalog with SKU search and location breakdown"

git add server/src/routes/warehouseRoutes.js server/src/routes/categoryRoutes.js client/src/pages/settings/WarehouseSettingsPage.jsx
git commit -m "feat(settings): implement warehouse and category management CRUD"

git add server/src/controllers/dashboardController.js server/src/routes/dashboardRoutes.js client/src/pages/dashboard/Dashboard.jsx
git commit -m "feat(dashboard): build real-time KPIs, dynamic multi-filters, and low-stock alert banner"

# STEP 3
git add server/src/routes/receiptRoutes.js client/src/pages/receipts/ReceiptsPage.jsx
git commit -m "feat(receipts): implement incoming stock receipts with atomic validation"

git add server/src/routes/deliveryRoutes.js client/src/pages/deliveries/DeliveryOrdersPage.jsx
git commit -m "feat(deliveries): implement outgoing delivery orders with negative stock prevention"

git add server/src/testStep3.js
git commit -m "test(step3): add automated test suite for receipt validation and negative stock prevention"

# STEP 4
git add server/src/routes/transferRoutes.js client/src/pages/transfers/TransfersPage.jsx
git commit -m "feat(transfers): implement multi-location internal transfers with atomic balance relocation"

git add server/src/routes/adjustmentRoutes.js client/src/pages/adjustments/AdjustmentsPage.jsx
git commit -m "feat(adjustments): implement physical count inventory reconciliation with automatic ledger sync"

git add server/src/routes/ledgerRoutes.js client/src/pages/move-history/MoveHistoryPage.jsx
git commit -m "feat(ledger): implement Move History audit trail with smart filters and CSV export"

git add server/src/testStep4.js README.md GIT-COMMITS-*.md
git commit -m "docs: full operational lifecycle test and comprehensive real-time architecture guide"

# PUSH
git remote add origin https://github.com/<USERNAME>/stocksense.git
git push -u origin main
```
