# Hisab Nafay Motors — Multi-Branch Dealership Management System

> A production-grade business management platform built for a multi-branch car dealership. Manages vehicle inventory, financial records, sales reporting, and currency conversion — replacing manual Excel-based workflows with an intelligent, automated system.

🚀 **Live System:** [nafaymotors-accounts-pkuc.vercel.app](https://nafaymotors-accounts-pkuc.vercel.app)

---

## Screenshots

### Dashboard Overview
![Dashboard](./screenshots/dashboard.png)
*Real-time overview of all dealership operations with key metrics and quick actions*

### Vehicle Inventory Management
![Inventory](./screenshots/inventory.png)
*Multi-branch vehicle stock tracking with real-time synchronization across all locations*

### Financial Records & Accounting
![Financial Records](./screenshots/accounting.png)
*Complete accounting ledger with transaction history and financial analysis*

### Sales Reports Generation
![Sales Reports](./screenshots/sales-reports.png)
*Auto-generated sales reports with filtering by branch, date range, and product type*

---

## Overview

Hisab Nafay Motors is a comprehensive dealership management platform built to digitalize and automate operations for a multi-branch car dealership. The system replaces fragmented Excel spreadsheets with an integrated, cloud-based solution.

**Problem Solved:**
- ❌ Manual Excel-based inventory tracking across 3+ branches
- ❌ Time-consuming manual sales report generation
- ❌ Inconsistent data across branches
- ❌ No real-time visibility into stock and finances
- ❌ Manual currency conversion for international sales

**Solution Provided:**
- ✅ Real-time inventory sync across all branches
- ✅ Automated sales report generation in minutes
- ✅ Single source of truth for all dealership data
- ✅ Live dashboard with key business metrics
- ✅ Automatic currency conversion support

---

## Key Features

### 🚗 Vehicle Inventory Management
- Track vehicle stock across multiple branches
- Real-time synchronization across all locations
- Record vehicle details: model, stock number, purchase price, current status
- Auto-update inventory when vehicles are sold or transferred
- Filter inventory by branch, status, or vehicle model
- Stock level alerts for low inventory items

### 🏢 Multi-Branch Operations
- Manage operations across multiple dealership branches
- Branch-specific inventory and sales tracking
- Centralized dashboard with branch-level breakdowns
- Transfer vehicles between branches
- Branch performance comparison reports

### 📊 Automated Sales Reports
- Auto-generate sales reports by date range
- Filter by branch, vehicle model, or salesperson
- Export reports in multiple formats
- Sales summary with total revenue, units sold, and margins
- Monthly, quarterly, and annual reporting
- Visual charts and graphs for analysis

### 💰 Financial Accounting
- Complete transaction ledger for all sales
- Track payments and outstanding balances
- Financial reports by period and branch
- Profit/loss analysis
- Account reconciliation tools
- Invoice and receipt generation

### 💵 Currency Conversion
- Support for multiple currencies
- Automatic exchange rate updates
- Convert transactions between currencies
- International sales tracking
- Currency-specific financial reports

### 📈 Business Analytics
- Key performance indicators (KPIs) dashboard
- Sales trends analysis
- Inventory turnover metrics
- Revenue forecasting
- Branch performance comparison
- Customer purchase history

### 🔐 User & Permission Management
- Role-based access control
- Admin, manager, and staff roles
- Activity logging and audit trail
- Secure authentication
- Password reset and recovery

---

## Tech Stack

![Next.js](https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white)
![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![MongoDB](https://img.shields.io/badge/MongoDB-4EA94B?style=for-the-badge&logo=mongodb&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)
![Vercel](https://img.shields.io/badge/Vercel-000000?style=for-the-badge&logo=vercel&logoColor=white)

| Layer | Technology |
|---|---|
| **Frontend** | Next.js 14, React.js, Tailwind CSS |
| **Backend** | Next.js Server Actions, Node.js |
| **Database** | MongoDB (Atlas) |
| **Authentication** | NextAuth.js / Custom JWT |
| **Hosting** | Vercel (Frontend + Serverless API) |
| **File Storage** | MongoDB GridFS or AWS S3 |
| **Reporting** | Chart.js / Recharts for visualizations |

---

## Database Schema

### Collections

**Vehicle**
- `id` — unique identifier
- `stockNumber` — vehicle stock/reference number
- `model` — vehicle model name
- `brand` — vehicle brand (Toyota, Honda, etc.)
- `year` — manufacturing year
- `purchasePrice` — cost price
- `sellingPrice` — current selling price
- `branch` — reference to Branch
- `status` — (Available, Sold, Reserved, Maintenance)
- `dateAdded` — when vehicle was added to inventory
- `lastUpdated` — last modification timestamp

**Branch**
- `id` — unique identifier
- `name` — branch location name
- `address` — physical address
- `city` — city
- `country` — country
- `phone` — contact number
- `manager` — branch manager name
- `createdAt`, `updatedAt`

**Sales**
- `id` — unique identifier
- `vehicleId` — reference to Vehicle sold
- `branchId` — reference to Branch where sold
- `buyerName` — customer name
- `salePrice` — final selling price
- `currency` — currency used (PKR, USD, etc.)
- `saleDate` — date of sale
- `paymentMethod` — (Cash, Check, Transfer, etc.)
- `commission` — salesperson commission
- `salesperson` — who made the sale
- `notes` — additional sale notes

**FinancialRecord**
- `id` — unique identifier
- `type` — (Income, Expense, Transfer)
- `amount` — transaction amount
- `currency` — transaction currency
- `description` — transaction description
- `branchId` — which branch
- `date` — transaction date
- `attachments` — receipts or invoices
- `approvedBy` — admin who approved
- `status` — (Pending, Approved, Rejected)

**User**
- `id` — unique identifier
- `email` — user email
- `password` — hashed password
- `fullName` — user full name
- `role` — (Admin, Manager, Staff)
- `branchId` — assigned branch (if applicable)
- `permissions` — array of permissions
- `lastLogin` — last login timestamp
- `createdAt`, `updatedAt`

---

## Project Structure

```
hisab-nafay-motors/
├── src/
│   ├── app/
│   │   ├── layout.js              # Root layout
│   │   ├── page.js                # Dashboard
│   │   ├── inventory/
│   │   │   ├── page.js
│   │   │   └── components/
│   │   │       ├── InventoryTable.js
│   │   │       ├── AddVehicleForm.js
│   │   │       └── VehicleFilters.js
│   │   ├── sales/
│   │   │   ├── page.js
│   │   │   └── components/
│   │   │       ├── SalesTable.js
│   │   │       ├── SalesReports.js
│   │   │       └── ReportGenerator.js
│   │   ├── accounting/
│   │   │   ├── page.js
│   │   │   └── components/
│   │   │       ├── FinancialLedger.js
│   │   │       ├── Transactions.js
│   │   │       └── AccountingReports.js
│   │   ├── branches/
│   │   │   ├── page.js
│   │   │   └── components/
│   │   │       ├── BranchManagement.js
│   │   │       └── BranchStats.js
│   │   └── api/
│   │       ├── vehicles/
│   │       ├── sales/
│   │       ├── accounting/
│   │       └── reports/
│   ├── components/
│   │   ├── Navbar.js
│   │   ├── Sidebar.js
│   │   ├── Dashboard.js
│   │   └── shared/
│   ├── lib/
│   │   ├── models/
│   │   │   ├── Vehicle.js
│   │   │   ├── Sale.js
│   │   │   ├── Branch.js
│   │   │   ├── User.js
│   │   │   └── FinancialRecord.js
│   │   ├── database.js
│   │   ├── auth.js
│   │   └── utils.js
│   └── styles/
│       └── globals.css
├── public/
├── .env.local                     # Environment variables
├── next.config.js
├── tailwind.config.js
└── package.json
```

---

## Getting Started

### Prerequisites
- Node.js 18+ 
- npm or yarn
- MongoDB account (free tier on Atlas)

### Installation

```bash
# Clone the repository
git clone https://github.com/your-username/hisab-nafay-motors.git
cd hisab-nafay-motors

# Install dependencies
npm install

# Create environment variables file
cp .env.example .env.local

# Add your configuration
# MONGODB_URI=your_mongodb_connection_string
# NEXTAUTH_SECRET=your_secret_key
# NEXTAUTH_URL=http://localhost:3000
```

### Development

```bash
# Start development server
npm run dev

# Open http://localhost:3000 in your browser
```

### Deployment

```bash
# Deploy to Vercel (recommended)
npm run build
vercel deploy

# Or build for production
npm run build
npm start
```

---

## Key Features in Detail

### Real-Time Inventory Sync
All branches see the same inventory in real-time. When a vehicle is sold at Branch A, Branch B immediately sees the updated stock.

### Automated Report Generation
Instead of manually creating Excel reports, the system generates comprehensive sales and financial reports in seconds with:
- Sales summary by branch
- Revenue analysis
- Top selling models
- Salesperson performance
- Profit margins

### Currency Conversion
Automatically convert and track international sales with live exchange rates. Track which sales were in which currency.

### Multi-Level Permissions
- **Admin:** Full system access, user management, branch management
- **Manager:** Branch-level access, can generate reports for their branch
- **Staff:** Can add vehicles and record sales only

### Activity Logging
Every action is logged with timestamp and user who performed it — complete audit trail.

---

## Performance Optimizations

- Indexed MongoDB queries for fast searches
- Pagination on large datasets
- Image optimization and lazy loading
- Server-side caching for reports
- CDN delivery via Vercel

---

## Security

- Secure authentication with hashed passwords
- Role-based access control (RBAC)
- Environment variable protection
- SQL/NoSQL injection prevention
- CSRF protection
- Rate limiting on API endpoints
- Encrypted sensitive data

---

## Built By

**Abdul Hannan** — Full Stack Developer | Next.js · Node.js · MongoDB · REST APIs

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/abdul-hannan-choudhary-866a493bb)
[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/abdul-hannan-SE)
[![Email](https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:contact.hannan100@gmail.com)

---

## License

This project is proprietary and built for Nafay Motors. All rights reserved.

---

*Built as a production system for a real business. Available for freelance full-stack and backend development projects.*
