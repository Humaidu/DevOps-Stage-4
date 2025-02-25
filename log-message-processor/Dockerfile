FROM python:3.10
WORKDIR /app
COPY requirements.txt .
RUN apt-get update && apt-get install -y libffi-dev libthrift-dev
RUN pip install --no-cache-dir -r requirements.txt
COPY . .
CMD ["python", "main.py"]
