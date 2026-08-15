# CK-01 — Vulnerable base image.
FROM python:3.11-slim

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY app.py .

# CK-02 / IV-05 fixed: Create a non-root user and switch to it
RUN useradd -m appuser
USER appuser

EXPOSE 5002

CMD ["python", "app.py"]
