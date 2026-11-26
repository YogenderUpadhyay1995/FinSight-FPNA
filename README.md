# FinSight FP&A — Financial Intelligence & Statement Analysis Platform

A full-stack Financial Statement Analysis Platform built with **React, TypeScript, Vite, Tailwind CSS, Recharts, ExcelJS, jsPDF, Express, and PostgreSQL / SQLite**.

## Key Features

- **Public Fintech Landing Page & Separate Analysis Workspace**: Clean marketing landing page with navigation, features, sample preview, FAQ, and contact form, plus a dedicated 10-section FP&A workspace.
- **Protected Excel Template Download & Upload**: Download a 6-sheet locked-structure `.xlsx` workbook (`Instructions`, `Company Information`, `Profit & Loss Statement`, `Balance Sheet`, `Cash Flow Statement`, `Notes to Accounts`) with worksheet protection, locked account heads/formulas, extendable year columns, and strict upload validation.
- **Deterministic Financial Engine**: Formula-based P&L, Balance Sheet (with separate Liquid Assets memo classification), Cash Flow (Direct & Indirect), 24+ financial ratios across 5 categories, and multi-year comparative analysis.
- **Notes to Financial Statements**: Paste structured notes, link them to specific statement accounts, view statements alongside linked notes, and let the AI Financial Analyst extract disclosed facts vs. interpretations.
- **Management Comments & Observations**: Attach user-provided commentary per period, statement, and account head, plus a final management conclusion.
- **Board-Ready PDF & Excel Exports**: 15-section PDF report with cover page, page numbers, validation results, ratios, AI insights, notes, and clearly separated management comments.

## Local Development

1. **Install dependencies**:
   ```bash
   npm install
   ```
2. **Configure environment (optional)**:
   Copy `.env.example` to `.env`. Locally, if `DATABASE_URL` / `POSTGRES_URL` is omitted, the app automatically uses local SQLite (`data/finsight.db`).
3. **Run development server** (Vite frontend + Express API):
   ```bash
   npm run dev
   ```
   Open `http://localhost:5173`.
4. **Run automated tests**:
   ```bash
   npm test
   ```
5. **Production build**:
   ```bash
   npm run build
   ```

## GitHub & Vercel Deployment

1. **Push to GitHub**:
   ```bash
   git init
   git add .
   git commit -m "Initial commit: FinSight FP&A Platform"
   git remote add origin <your-github-repo-url>
   git push -u origin main
   ```
   Ensure `.env` and `data/` are never committed (already excluded in `.gitignore`).
2. **Deploy on Vercel**:
   - Import the GitHub repository into **Vercel**.
   - Vercel automatically detects `vercel.json` (`npm run build` -> `dist/` + serverless `/api/index.ts`).
   - Add a managed PostgreSQL database (e.g., **Vercel Postgres**, **Neon**, or **Supabase**) and set `DATABASE_URL` (or `POSTGRES_URL`) in Vercel **Project Settings → Environment Variables**.
   - Deploy and verify `/api/health` returns `{"ok": true, "storage": "postgresql"}`.
