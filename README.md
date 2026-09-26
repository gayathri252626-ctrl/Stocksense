# 📦 StockSense - Next-Gen Inventory Management System (IMS)

> **Digitize stock operations within your business, replacing manual registers, paper forms, and fragmented Excel sheets with a centralized, real-time, easy-to-use application.**

---

## ⚡ Tech Stack

- **Frontend**: React 18, Vite, TailwindCSS, React Router v6, Lucide Icons, Socket.io-client
- **Backend**: Node.js, Express, Socket.io, Mongoose (MongoDB ODM)
- **Database**: MongoDB (includes automatic zero-config in-memory MongoDB fallback for instant local testing)
- **Authentication**: JWT, bcryptjs, role-based access control (`manager` and `staff`), and 6-digit OTP-based password reset (10-minute expiry; logs OTP directly to the server terminal console if SMTP is not configured)

---

## 🔑 Demo Login Credentials

The database comes pre-seeded with two accounts for instant testing:

| Role | Email | Password | Permissions |
| :--- | :--- | :--- | :--- |
| **Inventory Manager** | `manager@stocksense.com` | `password123` | Full administrative controls, warehouse settings, approvals |
| **Warehouse Staff** | `staff@stocksense.com` | `password123` | Transfers, picking, packing, shelving, counting |

*Note: You can also use the one-click demo login buttons directly on the Login screen, or create your own custom account via the **Sign Up** page.*

---

## 🚀 Quick Start Guide

### 1. Prerequisites
- **Node.js** (v18 or higher)
- **npm** (v9 or higher)
- *(Optional)* Local or Atlas MongoDB URI. If none is provided, StockSense will automatically launch an in-memory MongoDB database with zero configuration required!

### 2. Installation

Clone or open the project folder in your terminal:
```bash
cd stocksense
```

Install server dependencies:
```bash
cd server
npm install
```

Install client dependencies:
```bash
cd ../client
npm install
cd ..
```

### 3. Environment Configuration

Copy the example environment files:
```bash
# Server environment
cp server/.env.example server/.env

# Client environment
cp client/.env.example client/.env
```

#### Server Environment Variables (`server/.env`):
```ini
PORT=5000
NODE_ENV=development
CLIENT_URL=http://localhost:5173

# Database: Leave blank or set USE_MEMORY_DB=true for zero-config in-memory MongoDB
MONGODB_URI=
USE_MEMORY_DB=true

# Security
JWT_SECRET=stocksense_super_secure_jwt_secret_key_2026

# OTP Email (Leave blank to log OTP directly to the terminal console)
SMTP_HOST=
SMTP_PORT=587
SMTP_SECURE=false
SMTP_USER=
SMTP_PASS=
SMTP_FROM=noreply@stocksense.com
EXPOSE_OTP_IN_RESPONSE=true
```

#### Client Environment Variables (`client/.env`):
```ini
VITE_API_URL=http://localhost:5000/api
VITE_SOCKET_URL=http://localhost:5000
```

### 4. Seed the Database
Run the seed script to populate demo users, 2 warehouses, categories, 5 products, stock levels, and ledger history:
```bash
cd server
npm run seed
```

### 5. Running the Application

Open two terminal windows:

**Terminal 1 (Backend Server + Socket.io):**
```bash
cd server
npm run dev
# Server runs on http://localhost:5000
```

**Terminal 2 (Frontend React App):**
```bash
cd client
npm run dev
# App opens on http://localhost:5173
```

---

## 🧪 Automated Integration Tests

Run the comprehensive integration test suite verifying Signup, Login, OTP Generation, Password Reset, Dashboard Stats, and Socket.io client connections:
```bash
cd server
node src/testAuth.js
```

---

## 📐 Data Models Architecture

All required Mongoose models are located in `server/src/models/`:

1. **`User`**:
   - `name`, `email` (unique), `passwordHash`, `role` (`manager` \| `staff`), `timestamps`
2. **`OtpToken`**:
   - `email`, `code` (6 digits), `expiresAt` (10-minute automatic TTL index)
3. **`Warehouse`**:
   - `name`, `code` (unique, e.g. `MW-01`), `location`, `timestamps`
4. **`Category`**:
   - `name`, `description`, `timestamps`
5. **`Product`**:
   - `name`, `sku` (unique), `category` (ref), `unitOfMeasure`, `reorderPoint`, `timestamps`
6. **`StockLevel`**:
   - `product` (ref), `warehouse` (ref), `quantity`, compound unique index on `(product, warehouse)`
7. **`Receipt`** *(Incoming Goods)*:
   - `receiptNumber`, `supplier`, `warehouse` (ref), `lines: [{product, qty}]`, `status` (`draft` \| `waiting` \| `ready` \| `done` \| `cancelled`)
8. **`DeliveryOrder`** *(Outgoing Goods)*:
   - `orderNumber`, `customer`, `warehouse` (ref), `lines: [{product, qty}]`, `status` (`draft` \| `waiting` \| `ready` \| `done` \| `cancelled`)
9. **`InternalTransfer`** *(Inter-facility movements)*:
   - `transferNumber`, `fromWarehouse` (ref), `toWarehouse` (ref), `lines: [{product, qty}]`, `status`
10. **`Adjustment`** *(Inventory Count Reconciliation)*:
    - `adjustmentNumber`, `product` (ref), `warehouse` (ref), `systemQty`, `countedQty`, `diff`, `reason`, `status`
11. **`StockLedger`** *(Immutable Audit Trail)*:
    - `product` (ref), `warehouse` (ref), `qtyChange`, `type` (`receipt` \| `delivery` \| `transfer_in` \| `transfer_out` \| `adjustment` \| `initial`), `refDocId`, `timestamp`

---

## 🧭 Navigation & Layout Structure

The application features a sleek left sidebar navigation layout:
- 📊 **Dashboard**: Real-time KPI counters (Total Products, Low Stock Watchlist, Pending Receipts, Pending Deliveries, Scheduled Transfers), dynamic filter bar, operations launchpad, and live movement history.
- 📦 **Products**: Master product catalog with SKU search, unit of measure, location availability, and reorder point thresholds.
- 📥 **Receipts**: Inbound shipment management from suppliers.
- 📤 **Delivery Orders**: Outbound picking, packing, and validation for customer fulfillment.
- 🔁 **Internal Transfers**: Stock transfers between facilities (e.g., Main Store &rarr; Production Floor).
- ⚖️ **Stock Adjustments**: Reconciling physical counts vs. system recorded quantities.
- 📜 **Move History**: Complete, chronologically ordered Stock Ledger audit log.
- ⚙️ **Settings > Warehouse**: Facility registry and location management.
- 👤 **Profile Menu (Left Sidebar Bottom)**:
  - **My Profile**: View role permissions, user details, and security settings.
  - **Logout**: Clears session token and safely exits to the login screen.

---

## 🔐 OTP-Based Password Reset Flow

1. Click **Forgot password?** on the login screen.
2. Enter your registered email address (`manager@stocksense.com` or custom).
3. Click **Generate 6-Digit OTP**.
4. Check your server terminal console. A formatted log will appear:
   ```
   ========================================================
     [STOCKSENSE OTP VERIFICATION CODE]
     Target Email : manager@stocksense.com
     OTP Code     : >>>  778013  <<<
     Validity     : 10 minutes
   ========================================================
   ```
5. Enter the 6-digit code on the Reset Password page along with your new password.
6. Once submitted, your password is encrypted with bcrypt and updated in MongoDB, and the used OTP is automatically invalidated.
