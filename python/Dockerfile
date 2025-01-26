FROM python:3.12-slim

WORKDIR /app/api

# Copy requirements and install dependencies
COPY ./python/requirements.txt ./
RUN pip install --no-cache-dir -r requirements.txt

# Copy application code
COPY ./python/ .

# Copy Labels
COPY labels.txt /app/

# Expose the application port
EXPOSE 8000

# Run the application
CMD ["python", "main.py"]