# SUtore

SUtore is a full-stack e-commerce application built with:
- Django + Django REST Framework (backend)
- React (frontend)
- SQLite (default development database)

The project includes customer shopping flows and manager dashboards for product and sales operations.

## Features

- User registration, login, and profile updates
- Product browsing, category filtering, searching, and sorting
- Cart management and checkout flow
- Order history and order cancellation
- Wishlist and notifications
- Product reviews and rating
- Invoice generation (PDF) and invoice reporting
- Refund request workflow
- Role-based manager panels:
- `product_manager`: product/category/comment/stock/delivery management
- `sales_manager`: discount tools, refund approvals, invoice and revenue views

## Tech Stack

- Backend: Django 5, Django REST Framework, django-cors-headers
- Frontend: React 18, React Router
- Reporting/Charts: matplotlib
- PDF: pdfkit / wkhtmltopdf

## Repository Structure

- `backend/`: Django project (`ecommerce`) and app (`store`)
- `frontend/`: React app
- `requirements.txt`: Python dependencies
- `backend/db.sqlite3`: local development database
- `backend/media/`: uploaded product images, generated invoices, charts

## Local Setup

### 1. Backend (Django)

```bash
cd backend
python -m venv .venv
# Windows PowerShell
.\.venv\Scripts\Activate.ps1
# macOS/Linux
# source .venv/bin/activate

pip install -r ..\requirements.txt
python manage.py migrate
python manage.py runserver
```

Backend runs at `http://127.0.0.1:8000`.

### 2. Frontend (React)

In a second terminal:

```bash
cd frontend
npm install
npm start
```

Frontend runs at `http://localhost:3000`.

## Running Tests

Backend tests:

```bash
cd backend
python manage.py test
```

Frontend tests:

```bash
cd frontend
npm test
```

## API Notes

- Main endpoints are defined in `backend/store/urls.py`.
- The frontend currently calls the backend directly via `http://127.0.0.1:8000/...`.
- Protected endpoints use HTTP Basic Auth (credentials are stored in browser local storage by the current frontend flow).

## Important Development Notes

- `backend/ecommerce/settings.py` currently contains SMTP credentials directly in source. Move these to environment variables before deployment.
- This repository includes local development artifacts (`db.sqlite3`, generated media files, PDF/chart outputs).
- `wkhtmltopdf` binaries are bundled under `backend/wkhtmltopdf/`; verify executable availability on your OS if PDF generation fails.
