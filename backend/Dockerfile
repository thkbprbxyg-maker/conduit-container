FROM python:3.12-slim AS runtime

WORKDIR /app

# System deps (optional, safe default)
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
  && rm -rf /var/lib/apt/lists/*

# Install python deps
COPY requirements.txt /app/requirements.txt
RUN pip install --upgrade pip && \
    pip install --no-cache-dir --default-timeout=100 --retries=10 -r requirements.txt

# Copy app
COPY . /app

# Make sure gunicorn exists (if not in requirements.txt)
RUN pip show gunicorn >/dev/null 2>&1 || pip install --no-cache-dir gunicorn

ENV PORT=8000
EXPOSE 8000

# IMPORTANT: Replace the module below with YOUR WSGI module.
# Django example: projectname.wsgi:application
# Flask example: wsgi:app
ENV GUNICORN_APP_MODULE=REPLACE_ME

CMD ["sh","-c","gunicorn ${GUNICORN_APP_MODULE} --bind 0.0.0.0:${PORT} --workers 3 --timeout 120"]