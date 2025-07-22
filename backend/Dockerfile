FROM python:3.10-slim

# Install dependencies
RUN apt-get update && apt-get install -y tesseract-ocr poppler-utils && \
    rm -rf /var/lib/apt/lists/*

WORKDIR /app
COPY . .

RUN pip install --no-cache-dir -r requirements.txt

CMD ["gunicorn", "app:app", "--bind", "0.0.0.0:$PORT"]

