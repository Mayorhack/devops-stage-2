# Use an official Python runtime as a parent image
FROM python:3.10-slim

# Set the working directory in the container
WORKDIR /app

# Copy the pyproject.toml, poetry.lock, prestart.sh, and alembic.ini files to the container
COPY pyproject.toml poetry.lock prestart.sh alembic.ini /app/

# Copy the rest of the application code to the container
COPY . /app

# Install Poetry
RUN pip install poetry

# Install dependencies
RUN poetry install

# Install dos2unix to convert line endings
RUN apt-get update && apt-get install -y dos2unix

# Convert line endings for prestart.sh and backend_pre_start.py
RUN dos2unix /app/prestart.sh /app/app/backend_pre_start.py
# Run the prestart script

# Expose the port that FastAPI will run on
EXPOSE 8000
# Command to run the application with prestart so that the db is created before running app
CMD ["bash", "-c", "poetry run bash ./prestart.sh && poetry run uvicorn app.main:app --host 0.0.0.0 --port 8000"]

