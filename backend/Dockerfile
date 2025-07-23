FROM python:3.10-slim

# Install system dependencies for pdf2image (poppler-utils), pytesseract (tesseract-ocr),
# and general image processing libraries (libgl1, libgstreamer-plugins-base1.0-0)
RUN apt-get update && \
    apt-get install -y \
    tesseract-ocr \
    poppler-utils \
    libgl1 \
    libgstreamer-plugins-base1.0-0 && \
    rm -rf /var/lib/apt/lists/*

# Set the working directory in the container
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY requirements.txt .
COPY . .

# Install any needed packages specified in requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# Make port 8001 available to the world outside this container
EXPOSE 8001

# Run the application using gunicorn
CMD ["gunicorn", "app:app", "--bind", "0.0.0.0:$PORT"]
