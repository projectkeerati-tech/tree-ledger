# สมุดเงินใต้ร่มไม้ — อาณาเขตการเงิน

Thai offline PWA with a fan-made Jujutsu Kaisen themed illustration generated for this project. Not an official Moneypod/MAPPA app.

Features: income/expenses, categories, wallets/transfers, tags/images, savings goals, installment schedules, borrowing/lending, daily/category/month budgets, calendar/reports, CSV, print/PDF, JSON restore with duplicate protection, local PIN screen lock, local Thai/English neural OCR, optional Google Drive app-data backup.

Records remain in IndexedDB by default. Google Drive backups upload financial JSON only after the user connects and authorizes the app. No paid API/backend. Google OAuth setup is required: see GOOGLE-DRIVE-SETUP.md. Backups run while app is open, online and authorization is valid; not background iOS synchronization. JSON and IndexedDB are not encrypted. PIN is an interface lock, not encryption or Face ID.

OCR assets: Tesseract.js 6.0.1, core 6.0.0, Thai/English traineddata. GitHub Actions downloads pinned assets and verifies SHA256 before deployment. OCR models are loaded on first use and need internet then; ordinary bookkeeping works offline after app-shell caching. Receipt images are processed locally, not sent to an OCR API. OCR is fallible: users review fields before saving. Current scanner processes one receipt at a time, not automatic item-by-item categorization or batch scanning.

Deploy: GitHub Pages Source = GitHub Actions. Workflow deploy.yml builds a static artifact on push to main. No additional paid services or secrets required for deployment.

Limits: 10,000 transactions, 1,000 categories, 24 MB formatted backup, 10 MB combined encoded receipt images. Daily reminders run only while app is open. Native Face ID and guaranteed background notifications are not provided by this PWA.

Data migration: version-1 backups and the original tree-ledger IndexedDB are accepted; existing entries default to the main wallet. Close old tabs and reopen the app after updating. Back up JSON before upgrading and before clearing website data.
