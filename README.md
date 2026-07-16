# 🏥 Personalized Healthcare Dashboard (MTE Health Portal)

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![TypeScript](https://img.shields.io/badge/TypeScript-v5.x-blue?logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![React](https://img.shields.io/badge/React-v19.x-blue?logo=react&logoColor=61DAFB)](https://react.dev/)
[![Vite](https://img.shields.io/badge/Vite-v7.x-646CFF?logo=vite&logoColor=white)](https://vite.dev/)
[![Express](https://img.shields.io/badge/Express-v5.x-lightgrey?logo=express&logoColor=white)](https://expressjs.com/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind%20CSS-v4.x-38B2AC?logo=tailwindcss&logoColor=white)](https://tailwindcss.com/)

An advanced, interactive, and personalized digital health portal integrating tailored patient tracking and clinical management capabilities. Designed to bridge the gap between healthcare data and active patient care, this dashboard offers highly specialized interfaces for both **Patients** and **Healthcare Practitioners (Doctors)**.

---

## 🌟 Key Features

### 👤 Patient Dashboard
* **📊 Holistic Health Scoring:** Visually engaging interface showing current daily metrics, health scores, and progress trackers.
* **🩺 Real-Time Vitals Tracking:** Dynamic charts powered by Recharts visualizing blood pressure, blood glucose, heart rate, oxygen levels, and temperature history.
* **💊 Intelligent Medications Management:** Log daily medication intake, monitor dosage amounts, schedule frequencies, refill statuses, and view prescribing physician logs.
* **🔬 Lab Results Center:** Download, inspect, and track critical medical laboratory findings (e.g., blood work, lipids) complete with automated diagnostic range and status tags.
* **📅 Interactive Checkup Booking & Scheduling:** Book medical appointments, view scheduled sessions, and handle cancellations with logged reason fields.
* **🏃‍♂️ Activity & Workout Logging:** Dedicated `/activity` tracking step goals, active calorie burns, and exercise minutes.
* **🥗 Nutritional & Diet Planner:** Detailed `/diet` logging calorie target progress, active tracking, water intake, and customized macronutrient balances.
* **🤖 Personal AI Health Insights:** Algorithmic-based feedback, wellness tips, and warnings tailored specifically to logged vitals and history.

### ⚕️ Doctor Dashboard
* **📋 Patient Directory ("My Patients"):** Interactive view listing all registered patients with statuses (Active, Completed, Scheduled) and detailed clinical summaries.
* **🔍 Complete Medical Records Review:** Gain full visibility into a patient's historical diagnoses, vitals, active prescriptions, and past clinic visits.
* **💬 Clinical Communication:** Secure, interactive messaging channel directly with individual patients for remote assessments, prescription updates, and advice.

### ✉️ Real-Time Alerts & Integration
* **📧 Automated Nodemailer Communications:** Instantly dispatches beautifully stylized email receipts upon logins or critical changes (e.g., medical registrations and schedule adjustments).
* **📝 Detailed Delivery Auditing:** Full local logging file (`server/email_delivery.log`) tracks all outgoing communications, timestamp records, error logs, and delivery status checks.

---

## 🛠️ Tech Stack & Architecture

This repository contains a full-stack JavaScript/TypeScript application configured for rapid scaling, rich client state, and secure local management:

### Frontend
* **UI/Framework:** React 19 (TypeScript), Tailwind CSS (v4) with custom tailwind-animate components.
* **Routing:** React Router DOM v6.
* **Data Fetching:** TanStack React Query (v5) providing seamless asynchronous cache operations.
* **Charts/Visuals:** Recharts & Framer Motion for high-fidelity animations.
* **Theme Support:** Tailwind Dark Mode with instant theme toggling.

### Backend
* **API/Server:** Express.js 5.x.
* **Database/ORM:** Drizzle ORM connecting to PostgreSQL database structures (`shared/schema.ts`).
* **Authentication:** Passport.js (Local Strategy) managing credential encryption and persistent sessions.
* **Utilities:** Nodemailer for automated diagnostic logging and client communications.

---

## 📁 Repository Structure

```
├── client/                     # Frontend Application (React, Tailwind, Vite)
│   ├── public/                 # Static Assets (favicon, icons, portal logos)
│   ├── src/
│   │   ├── components/         # Reusable UI Blocks (Shadcn primitives, charts, layouts)
│   │   ├── hooks/              # Custom React Hooks (toasts, utilities)
│   │   ├── lib/                # API helpers, state/data controllers (localApi.ts)
│   │   ├── pages/              # Portal Layouts (Dashboard, Diet, Activity, LabResults, etc.)
│   │   ├── App.tsx             # Global Route Mapping
│   │   └── main.tsx            # Frontend Entry Point
│   └── index.html
├── server/                     # Backend API & Express Architecture
│   ├── index.ts                # Express Main Server Entry point
│   ├── routes.ts               # Core API Endpoints (Emailing, Auditing, Messaging)
│   ├── static.ts               # SPA Routing Static Deliveries
│   ├── storage.ts              # Data Store Controllers
│   └── vite.ts                 # Dev HMR Server Handlers
├── shared/
│   └── schema.ts               # Drizzle PostgreSQL Database Schemas
├── types/                      # Common TypeScript definitions
├── package.json                # Project Node.js Manifest
└── README.md                   # Project Documentation
```

---

## 🚀 Getting Started

Follow these steps to configure your environment and run the dashboard locally.

### 📋 Prerequisites
* **Node.js** (v18.x or above recommended)
* **npm** or **Yarn**

### ⚙️ Installation

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/Aneesh2507/Personalized-Healthcare-Dashboard.git
   cd Personalized-Healthcare-Dashboard
   ```

2. **Install Dependencies:**
   ```bash
   npm install
   ```

3. **Configure Environment Variables:**
   Create a `.env` file in the root directory (or use environment configurations) to set up your mailer and session configuration:
   ```env
   # SMTP Server details for Automated Email Deliveries (Nodemailer)
   SMTP_HOST=your-smtp-host
   SMTP_PORT=587
   SMTP_USER=your-email@example.com
   SMTP_PASS=your-secure-password

   # Session Secret for Passport.js User Sessions
   SESSION_SECRET=your-random-session-secret-key

   # Database Connection String
   DATABASE_URL=postgresql://user:password@localhost:5432/healthcare_db
   ```

### 💻 Running the Application

* **Development Mode:**
  Runs the client (Vite) and server (Express) concurrently with hot-reloading support:
  ```bash
  npm run dev
  ```
  *The app will automatically start on `http://localhost:5000`.*

* **Database Push (Drizzle):**
  If you have configured PostgreSQL and want to push the table structure defined in `shared/schema.ts`:
  ```bash
  npm run db:push
  ```

* **Production Build:**
  Compiles the TypeScript frontend and backend for production deployment:
  ```bash
  npm run build
  npm start
  ```

---

## 🔬 Interactive Workflows

### 🤝 Authentication & Role Selection
* Navigate to the `/login` page.
* You can sign up as a **Patient** or a **Doctor**.
* Validation rules verify valid email structures, robust passwords, and standard mobile inputs.
* Logging in triggers a transactional confirmation email with full credentials details.

### 📈 Clinical Updates (Doctor to Patient)
1. Log in with a **Doctor** profile.
2. Select a patient from **My Patients**.
3. Inspect historical vitals, review active lab panels, or send targeted advisory messages.
4. Log back in as the **Patient** to view updated diagnostic summaries, updated medication plans, or clinical notes in real time.

---

## 📝 License

Distributed under the MIT License. See `LICENSE` or the badge at the top for more information.

---

## 👥 Contributors

* **Aneesh Vojjala** ([GitHub Profile](https://github.com/Aneesh2507)) - Medical Engineering & AI Solutions Developer.
