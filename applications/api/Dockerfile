FROM python:3.11-slim

WORKDIR /app

ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

RUN apt-get update \
  && apt-get install -y --no-install-recommends gcc \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/*

COPY requirements.txt .

RUN pip install --no-cache-dir --upgrade pip && \
  pip install --no-cache-dir -r requirements.txt

COPY . .

ENV PORT=5000

EXPOSE 5000

CMD ["python", "-m", "applications.api.src.api"]