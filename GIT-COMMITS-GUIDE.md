# StockSense — Step 1 Git Commits & GitHub Upload Guide

This directory has been organized and initialized with a **complete 5-commit Git history** representing **Step 1: Foundation, Data Models & Authentication**.

---

## 📋 The 5 Step-by-Step Commits for Step 1

### Commit 1: Project Scaffolding & Monorepo Setup
- **Commit Message**:
  ```text
  chore: initialize project scaffolding and workspace configuration

  - Add root package.json and workspace scripts
  - Configure .gitignore for Node, Vite, and environment files
  - Add comprehensive architecture and setup README
  ```
- **Files Included**:
  - `.gitignore`
  - `package.json`
  - `README.md`

---

### Commit 2: Server Architecture, Database & All Mongoose Models
- **Commit Message**:
  ```text
  feat(server): setup Express server, MongoDB connection, and Mongoose schemas

  - Configure MongoDB connection with automatic in-memory fallback
  - Define 11 core Mongoose schemas: User, OtpToken, Warehouse, Category, Product, StockLevel, StockLedger, Receipt, DeliveryOrder, InternalTransfer, Adjustment
  - Create database seed script with manager and staff demo accounts
  ```
- **Files Included**:
  - `server/package.json`
  - `server/.env.example`
  - `server/.env`
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

---

### Commit 3: Authentication API, Role Guards & OTP Password Reset
- **Commit Message**:
  ```text
  feat(auth): implement JWT authentication, role guards, and OTP password recovery

  - Implement signup, login, and token verification with bcrypt & JWT
  - Build 6-digit OTP password reset workflow with 10-minute expiry
  - Add role-based access control middleware (manager vs staff)
  - Setup Socket.io real-time server and auth verification test script
  ```
- **Files Included**:
  - `server/src/controllers/authController.js`
  - `server/src/controllers/dashboardController.js`
  - `server/src/routes/authRoutes.js`
  - `server/src/routes/dashboardRoutes.js`
  - `server/src/routes/warehouseRoutes.js`
  - `server/src/routes/productRoutes.js`
  - `server/src/middleware/auth.js`
  - `server/src/middleware/errorHandler.js`
  - `server/src/socket.js`
  - `server/src/server.js`
  - `server/src/testAuth.js`

---

### Commit 4: Client Tooling, TailwindCSS Theme & Navigation Layout
- **Commit Message**:
  ```text
  feat(client): configure Vite, TailwindCSS design system, and core app layout

  - Configure Vite 5 build tool, TailwindCSS, PostCSS, and Autoprefixer
  - Build dark/light theme foundation, typography, and glassmorphic styles
  - Create responsive Layout with collapsible Sidebar and modern Navbar
  - Configure Axios HTTP interceptor and Auth/Socket React contexts
  ```
- **Files Included**:
  - `client/package.json`
  - `client/vite.config.js`
  - `client/tailwind.config.js`
  - `client/postcss.config.js`
  - `client/index.html`
  - `client/.env.example`
  - `client/.env`
  - `client/src/index.css`
  - `client/src/api/axios.js`
  - `client/src/context/AuthContext.jsx`
  - `client/src/context/SocketContext.jsx`
  - `client/src/components/layout/Navbar.jsx`
  - `client/src/components/layout/Sidebar.jsx`
  - `client/src/components/layout/Layout.jsx`

---

### Commit 5: Client Authentication Pages & Protected Routing
- **Commit Message**:
  ```text
  feat(client): implement authentication pages, OTP recovery flow, and protected routing

  - Build Login page with demo credentials quick-fill buttons
  - Build Signup page with role selection (Manager / Staff)
  - Build Forgot Password & Reset Password OTP verification pages
  - Implement protected route guards and core navigation pages
  - Wire React Router v6 in App.jsx and mount in main.jsx
  ```
- **Files Included**:
  - `client/src/pages/auth/Login.jsx`
  - `client/src/pages/auth/Signup.jsx`
  - `client/src/pages/auth/ForgotPassword.jsx`
  - `client/src/pages/auth/ResetPassword.jsx`
  - `client/src/pages/dashboard/Dashboard.jsx`
  - `client/src/pages/products/ProductsPage.jsx`
  - `client/src/pages/receipts/ReceiptsPage.jsx`
  - `client/src/pages/deliveries/DeliveryOrdersPage.jsx`
  - `client/src/pages/transfers/TransfersPage.jsx`
  - `client/src/pages/adjustments/AdjustmentsPage.jsx`
  - `client/src/pages/move-history/MoveHistoryPage.jsx`
  - `client/src/pages/settings/WarehouseSettingsPage.jsx`
  - `client/src/pages/profile/ProfilePage.jsx`
  - `client/src/App.jsx`
  - `client/src/main.jsx`

---

## 🚀 How to Upload to GitHub

### Option 1: Push Existing Pre-Initialized Commits (Fastest)

Since this folder **already contains the initialized `.git` repository with all 5 commits**, you just need to link it to your GitHub repository:

1. Create a new empty repository on **[github.com/new](https://github.com/new)** (do not check "Add README" or ".gitignore").
2. Open PowerShell or Command Prompt in this folder:
   ```powershell
   cd "C:\Users\Gokulram M\Downloads\stocksense-step1"
   ```
3. Set your remote URL and push:
   ```bash
   git branch -M main
   git remote add origin https://github.com/<YOUR-USERNAME>/<YOUR-REPO-NAME>.git
   git push -u origin main
   ```
*All 5 commits will instantly appear on your GitHub repository!*

---

### Option 2: Run the Manual Git Commands Step-by-Step

If you want to manually run the git commands from scratch, run:

```bash
# 1. Initialize
git init -b main

# 2. Commit 1: Scaffolding
git add .gitignore package.json README.md
git commit -m "chore: initialize project scaffolding and workspace configuration"

# 3. Commit 2: Database and Models
git add server/package.json server/.env.example server/src/config/db.js server/src/models/ server/src/seed.js
git commit -m "feat(server): setup Express server, MongoDB connection, and Mongoose schemas"

# 4. Commit 3: Auth API & Backend
git add server/src/controllers/ server/src/routes/ server/src/middleware/ server/src/socket.js server/src/server.js server/src/testAuth.js
git commit -m "feat(auth): implement JWT authentication, role guards, and OTP password recovery"

# 5. Commit 4: Client Layout & Theme
git add client/package.json client/vite.config.js client/tailwind.config.js client/postcss.config.js client/index.html client/.env.example client/src/index.css client/src/api/ client/src/context/ client/src/components/
git commit -m "feat(client): configure Vite, TailwindCSS design system, and core app layout"

# 6. Commit 5: Client Auth Pages & Router
git add client/src/pages/ client/src/App.jsx client/src/main.jsx
git commit -m "feat(client): implement authentication pages, OTP recovery flow, and protected routing"

# 7. Push to GitHub
git remote add origin https://github.com/<YOUR-USERNAME>/<YOUR-REPO-NAME>.git
git push -u origin main
```
