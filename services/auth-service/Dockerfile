# CK-01 — Vulnerable base image. python:3.9-slim carries outdated system libraries.
FROM python:3.12-alpine

WORKDIR /app

# Update system packages and install curl for healthcheck
RUN apk update && apk upgrade && \
    apk add --no-cache curl && \
    rm -rf /var/cache/apk/*

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY app.py .

# CK-02 / IV-05 fixed: Create a non-root user and switch to it
RUN apk add --no-cache shadow && \
    useradd -m appuser
USER appuser

EXPOSE 5001

CMD ["python", "app.py"]
