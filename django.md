# Django

## Django Rest Framework

- Writing custom permission classes
  - [Custom permissions](https://www.django-rest-framework.org/api-guide/permissions/#custom-permissions)
  - [Custom permission classes](https://testdriven.io/blog/custom-permission-classes-drf/)

## Migrations

- django.db.migrations.exceptions.InconsistentMigrationHistory
  - python manage.py dbshell
  - \c <database_name>;
  - select * from django_migrations where app='<app>';
  - delete from django_migrations where id=<migration_you_want_to_drop>;
