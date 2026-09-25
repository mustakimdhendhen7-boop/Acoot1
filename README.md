# Acoot Smart Books V5

Antideploy-ready Indian accounting application built around PostgreSQL and persistent S3-compatible receipt storage.

## Included
- Persistent PostgreSQL authentication and sessions
- Multi-company isolation
- Company GSTIN / financial-year / currency fields
- Double-entry ledger engine with balanced debit/credit validation
- Voucher types: Sales, Purchase, Receipt, Payment, Contra, Journal, Credit Note, Debit Note
- Ledger management and default accounting ledgers
- Customers and suppliers
- Products with HSN/SAC, GST rate and stock fields
- GST input/output tracking and basic GST report
- Profit & Loss dashboard/report
- Receipt/invoice upload to persistent S3-compatible storage
- Optional AI extraction from receipt/invoice images using OpenAI vision API
- No local database and no local production upload directory

## Antideploy
Upload/connect this project and let Antideploy analyze it. The project is intentionally aligned with Antideploy's S3 environment-variable convention so its object-storage dependency can be provisioned without asking you to paste AWS credentials into the app configuration.

Antideploy-created variables to accept:
- `DATABASE_URL` — PostgreSQL connection
- `AWS_S3_BUCKET` — persistent receipt bucket
- `AWS_REGION` — object-storage region
- `AWS_S3_ENDPOINT` — S3-compatible endpoint when provided
- `AWS_ACCESS_KEY_ID` / `AWS_SECRET_ACCESS_KEY` — consumed by the AWS SDK's default credential provider chain; they are **not hard-coded or read directly by Acoot**

Do not invent AWS values. If Antideploy has not provisioned object storage yet, re-analyze the project after upload and use the S3 dependency it detects. The local filesystem is never used for production receipt storage.

Optional AI:
- `OPENAI_API_KEY`
- `OPENAI_MODEL` (default `gpt-4o-mini`)

The application runs migrations automatically at startup.

## Local
```bash
npm install
npm start
```

A PostgreSQL database is required. For AI receipt extraction, configure `OPENAI_API_KEY` and S3 storage.
