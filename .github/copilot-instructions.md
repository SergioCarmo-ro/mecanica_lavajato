# Copilot Instructions for mecanica_lavajato

## Project Overview
- This is a Django-based web application for managing a car wash business ("mecânica lavajato").
- The project is organized into Django apps: `clientes` (customers), `servicos` (services), and the main project config `mecajato`.
- Data is stored in a local SQLite database (`db.sqlite3`).

## Key Components
- `clientes/`: Handles customer-related models, views, templates, and migrations.
- `servicos/`: Handles service-related models, forms, views, templates, and migrations. Includes business logic for car wash services.
- `mecajato/`: Django project settings, URLs, and WSGI/ASGI entry points.
- `templates/`: Shared base template and static assets (CSS/JS) organized by feature.

## Developer Workflows
- **Run the server:**
  ```powershell
  python manage.py runserver
  ```
- **Apply migrations:**
  ```powershell
  python manage.py migrate
  ```
- **Create migrations:**
  ```powershell
  python manage.py makemigrations
  ```
- **Run tests:**
  ```powershell
  python manage.py test
  ```
- **Static files:** Static assets are under `templates/static/` and referenced in templates using Django's `{% static %}` tag.

## Project Conventions
- Templates for each app are under `app/templates/` (e.g., `clientes/templates/clientes.html`).
- Static files are grouped by feature inside `templates/static/` (e.g., `servicos/css/listar_servico.css`).
- Use Django's class-based views and forms where possible.
- Migrations are tracked per app in `migrations/` folders.
- All business logic should reside in the appropriate app (`clientes` or `servicos`).

## Integration Points
- No external APIs or services are integrated by default.
- All data flows through Django ORM models and views.
- The project uses only standard Django dependencies (see `requirements.txt`).

## Examples
- To add a new service type, update `servicos/models.py` and create a migration.
- To customize the customer list UI, edit `clientes/templates/clientes.html` and the related static files.

## References
- Main entry: `manage.py`
- Settings: `mecajato/settings.py`
- URLs: `mecajato/urls.py`, `clientes/urls.py`, `servicos/urls.py`

---
For questions about project structure or workflows, review the relevant app directory or ask for clarification.
