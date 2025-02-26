# Use a smaller Alpine-based Python image
FROM python:3.10-alpine

# Set the working directory
WORKDIR /app

# Copy only the requirements file to leverage Docker caching
COPY requirements.txt .

# Install dependencies using Alpine's package manager (apk)
RUN apk add --no-cache libffi-dev thrift-dev build-base && \
    pip install --no-cache-dir -r requirements.txt && \
    rm -rf /root/.cache/pip

# Copy the application files
COPY . .

# Set the default command to run the application
CMD ["python", "main.py"]
