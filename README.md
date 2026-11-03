# Piki Ora Medical Centre - Django REST Framework API

ISCG7420 Web Application Development - Assignment 2, Task 2 (backend)

Student: Adithyan Suji (Student ID: 1589957)

- Backend API: https://pikiora-clinic.onrender.com/api/
- React frontend repository: https://github.com/12adisuji05/ISCG7420-Assignment2-React

## Apps

- `clinic` - models (Doctor, Slot, Appointment)
- `api` - serializers, viewsets, permissions and URLs

## API endpoints

| Endpoint | Who can use it |
| --- | --- |
| `POST /api/register/` | Anyone - creates a patient and returns a token |
| `POST /api/auth/` | Anyone - username and password, returns a token |
| `GET /api/me/` | Logged-in user |
| `/api/doctors/` | Anyone can view, staff can add, edit and delete |
| `/api/slots/` (`?doctor=1`, `?available=true`) | Anyone can view, staff can add, edit and delete |
| `/api/appointments/` | Patients manage their own, staff manage all |
| `/api/patients/` | Staff only - view, edit and delete patient accounts |

Send the token in the header: `Authorization: Token <token>`

## Run on your computer

```
py -m venv venv
venv\Scripts\activate
pip install -r requirements.txt
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver
```

## Deploy to Render

The database is PostgreSQL hosted on Neon (free plan).

1. Create a Neon project and copy its connection string.
2. On Render: New > Blueprint > choose this repository.
3. Enter the Neon connection string for `DATABASE_URL` and a password for `DJANGO_SUPERUSER_PASSWORD`.

`build.sh` runs the migrations and creates the admin user on each deploy. The admin username is `admin`.

## References

- Django REST framework. (n.d.). *Authentication*. https://www.django-rest-framework.org/api-guide/authentication/
- Django REST framework. (n.d.). *Viewsets*. https://www.django-rest-framework.org/api-guide/viewsets/
- Django Software Foundation. (n.d.). *django-admin createsuperuser* (Version 5.2). https://docs.djangoproject.com/en/5.2/ref/django-admin/#createsuperuser
- Jazzband. (n.d.). *dj-database-url* [Computer software]. https://github.com/jazzband/dj-database-url
- Johnson, A. (n.d.). *django-cors-headers* [Computer software]. https://github.com/adamchainz/django-cors-headers
- Neon. (n.d.). *Connect from Django to Neon*. https://neon.com/docs/guides/django
- Render. (n.d.). *Deploy a Django app on Render*. https://render.com/docs/deploy-django
- WhiteNoise. (n.d.). *Using WhiteNoise with Django*. https://whitenoise.readthedocs.io/en/stable/django.html
