FROM python:slim

# Set working directory for the app
WORKDIR /app

# Copy requirements first to leverage Docker layer caching
COPY requirements.txt .

# Install dependencies without caching to keep image smaller
RUN pip install --no-cache-dir -r requirements.txt

# Copy all remaining application files
COPY . .

# Convert line endings from CRLF to LF and make the entrypoint script executable
RUN sed -i 's/\r$//' ./docker-entrypoint.sh && chmod +x ./docker-entrypoint.sh

# Create a volume for persistent data
VOLUME ["/app/data"]

# Set the entrypoint to the startup script
ENTRYPOINT ["./docker-entrypoint.sh"]

# Set default command to start the uvicorn web server
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]