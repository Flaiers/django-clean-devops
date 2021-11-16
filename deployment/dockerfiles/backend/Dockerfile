FROM python:latest

ENV PYTHONUNBUFFERED=1
ENV LEVEL=PRODUCTION

WORKDIR /opt/app

# copy web app to container
COPY django-template/ .

# update apt packages, install psql
RUN apt-get update && apt-get install -y --no-install-recommends postgresql-client

# create environment, install packages, makemigrations
RUN python -m venv env && . env/bin/activate && cd src/ && \
    pip install -U pip && pip install -r requirements.txt && \
    python manage.py makemigrations admin auth contenttypes sessions --name alter_db_table && \
    python manage.py makemigrations