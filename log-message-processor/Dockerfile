FROM python:3.10
WORKDIR /app
COPY requirements.txt .
RUN python3 -m venv /app/venv && \
    source /app/venv/bin/activate && \
    pip install -r requirements.txt
COPY . .
CMD ["python", "main.py"]
