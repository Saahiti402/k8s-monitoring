# Use Python base image
FROM python:3.9

# Set working directory
WORKDIR /app

# Copy files
COPY . .

# Install dependencies
RUN pip install flask

# Expose the service port
EXPOSE 5002

# Run the application
CMD ["python", "app.py"]

