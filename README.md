# Lunch On The Go

A Django web application prototype with account registration and sign-in flows, plus food-service interface assets.

## Current status

This checkout is incomplete: `e_food/urls.py` includes `main.urls`, but the `main/` app is not present in the repository tree. The application cannot start until that app is restored or the URL configuration is updated.

The project currently pins Django 3.0.4, which is no longer supported. Upgrade to a currently supported Django release before using this app in a public deployment. See the [Django supported versions](https://www.djangoproject.com/download/) page.

## Local configuration

The Django signing key is read from the `DJANGO_SECRET_KEY` environment variable. Never commit a real key or a `.env` file. For a local development shell, generate a fresh key:

```sh
export DJANGO_SECRET_KEY="$(python -c 'from django.core.management.utils import get_random_secret_key; print(get_random_secret_key())')"
export DJANGO_DEBUG=true
```

`DEBUG` is off by default. `ALLOWED_HOSTS` can be supplied as a comma-separated `DJANGO_ALLOWED_HOSTS` value; local development defaults to `localhost,127.0.0.1`.

After restoring the missing `main` app, create a virtual environment, install the pinned dependencies, migrate the database, and start Django:

```sh
python -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
python manage.py migrate
python manage.py runserver
```

On Windows, activate the virtual environment with `.venv\Scripts\activate`.

## Repository hygiene

Local virtual environments, Python bytecode, SQLite databases, and environment files are excluded from version control. User uploads and interface assets under `media/` are retained; check them before adding personal data.

